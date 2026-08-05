# SGW-005 — Security Audit (Shadvert)

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGW-005 |
| **Title** | Security Audit — ShadowGuard Shadvert |
| **Version** | 2.0 (delta) |
| **Date** | 2026-07-30 · **Delta** 2026-08-06 |
| **Scope** | Live `shadowguard-shadvert.site` + kód `ShadowGuard-Shadvert` (`main` + větev `ui/design-v2`) |
| **Status** | Delta re-pass Trust Sprint — P0 live OK; zbývají P1/P2 + Trust Engine |
| **Auditor** | Grok Build (lokální implementační vrstva) |

**Motto:** Bezpečnost vytváří důvěru. Audit bez nápravy je jen report.

---

## 0. Kontext a korekce

### Co Grok (chat) správně řekl
- Foundation je silná, ale **důvěra potřebuje i běžící bezpečný produkt**.
- Paralelní běh: dokumenty + security na existující appce.
- Live app už běží → riziko každý den.

### Co Grok (chat) neměl pravdu
- **Privátní repo `ShadowGuard-Shadvert` existuje** (private, last push 2026-07-27).  
  404 mohl být z jiného kontextu / neautentizovaného přístupu.  
  Kód je dostupný přes účet `jamajka666` a byl naklonován na Asus do  
  `~/Projects/ShadowGuard-Shadvert`.

### Stav Foundation (pro pořádek)
- Way (**SGF-002**) a Trust Principles (**SGF-008**) už existují.  
- Design Principles a Brand zbývají; Architecture až po security základu (souhlas s paralelním během).

---

## 1. Externí kontrola live webu

| Kontrola | Výsledek |
|----------|----------|
| HTTPS (Cloudflare) | Ano (HTTP/2) |
| `Strict-Transport-Security` | **Chybí** (nebo nepropisuje se z originu) |
| `Content-Security-Policy` | **Chybí** |
| `X-Frame-Options` / `frame-ancestors` | **Chybí** |
| `X-Content-Type-Options` | **Chybí** |
| `Referrer-Policy` | **Chybí** |
| `Permissions-Policy` | **Chybí** |
| `X-Powered-By: Express` | **Exponováno** (zbytečný fingerprint) |
| `GET /api/health` | Veřejné — OK pro monitoring (žádná citlivá data) |
| `GET /api/family/config` | Veřejné — jen verze/announcements — OK |
| `GET /api/family/devices` bez tokenu | **401** — admin auth funguje |
| `POST /api/analyze-ad` prázdné body | **400** — validace vstupu OK |
| `POST /api/family/heartbeat` bez `familyCode` | **`{"ok":true}`** — **KRITICKÉ** (viz §3) |

---

## 2. Repozitář a tajemství

| Kontrola | Výsledek |
|----------|----------|
| `.env` / `.env.local` v gitu | **Ne** (správně) |
| `.gitignore` pokrývá env + `data/*.json` | **Ano** |
| `.env.example` jen placeholdery | **Ano** |
| Historie gitu s reálnými klíči (rychlý scan) | **Nenalezeny** reálné AIza… / long secrets v commitech |
| `GEMINI` jen na serveru (`process.env`) | **Ano** — klíč ve frontendu nenačten |

**Doporučení:** i tak jednou pro jistotu `git log -p \| secrets` + rotace tokenů po jakémkoli podezření; secrets-backup soubor je v gitignore (dobré).

---

## 3. Nálezy (prioritizované)

### P0 — Kritické (opravit co nejdřív)

#### P0-1 Heartbeat bez rodinného kódu
**Kde:** `server.ts` — `POST /api/family/heartbeat`

```ts
if (FAMILY_CODE && familyCode && !familyCodeOk(familyCode)) {
```

Podmínka selže (a pustí request dál), když klient **nepošle** `familyCode`.  
**Ověřeno na live:** heartbeat s jen `deviceId` vrátil `ok: true`.

**Dopad:** kdokoliv na internetu může plnit `family.json` falešnými zařízeními (spam / DoS na DB / zmatek v adminu).

**Náprava:** pokud je `FAMILY_CODE` nastavený, **vyžadovat** platný kód; jinak 403. Pokud není nastavený, v produkci heartbeat raději vypnout.

---

#### P0-2 Veřejné `/api/analyze-ad` bez rate-limitu
**Kde:** `POST /api/analyze-ad` — žádná autentizace, žádný rate-limit.

**Dopad:**
- vyčerpání **Gemini** kvóty / peněz,
- zátěž CPU/TLS/WHOIS na domácím PC,
- body až **10 MB** (`express.json({ limit: '10mb' })`) + volitelný `imageBase64` → snadné zahlcení.

**Náprava:** `express-rate-limit` (globální + přísnější na analyze/ssl); zvážit menší limit body pro analyze; volitelně jednoduchý shared family token pro API (později).

---

#### P0-3 Chybí bezpečnostní HTTP hlavičky (Helmet)
**Kde:** celý Express app; live response bez CSP/HSTS/XFO/…

**Dopad:** clickjacking, MIME sniffing, slabší ochrana XSS, žádný HSTS z originu (CF může částečně pomoci, ale origin by měl posílat pořádně).

**Náprava:** `helmet` + rozumná CSP pro Vite/React assety; `app.disable('x-powered-by')`.

---

### P1 — Vysoké

#### P1-1 SSRF / síťové skeny přes SSL check
**Kde:** `checkSSLCertificate` / `getFullDomainSSLInfo` — `tls.connect` na hostname z uživatele; DNS lookup.

**Dopad:** útočník může nutit server připojovat se k interním IP / metadata službám (podle sítě) nebo skenovat port 443 v okolí. Domácí PC za CF tunnel stále otevírá odchozí TLS.

**Náprava (hotovo v kódu 2026-07-30):**  
- modul `src/utils/ssrfGuard.ts`  
- blokace private/reserved IP, localhost, `.local`/`.internal`, metadata hostnames  
- DNS resolve **všech** adres — pokud jakákoli je neveřejná → odmítnout  
- TLS connect na **veřejnou IP** + SNI = hostname  
- self-test: 127.0.0.1 / localhost blocked, example.com allowed  

**Deploy Lenovo:** ještě `git pull` + build (stejný postup jako P0).

---

#### P1-2 Veřejné `/api/check-domain-ssl` a `/api/scam-alerts`
Stejný abuse vektor jako analyze (méně Gemini, ale síť/CPU; scam-alerts volá Gemini).

**Náprava:** rate-limit (P0) + **in-memory cache** scam-alerts (default TTL 30 min, env `SCAM_ALERTS_CACHE_TTL_MS`, hlavička `X-Cache`). **Hotovo v kódu.**

---

#### P1-3 Sdílený `FAMILY_CODE` jako dlouhodobé „heslo“
Jeden kód pro celou rodinu v `localStorage` na tabletu.

**Dopad:** kdokoli s kódem čte/posílá history; kód se těžko rotuje po úniku.

**Náprava (později):** per-device tokeny, rotace, krátká expirace; zatím: silný náhodný kód + rotace při podezření.

---

#### P1-4 Admin token v `sessionStorage`
**Kde:** `AdminPanel.tsx` — Bearer v sessionStorage.

**Dopad:** XSS → krádež admin tokenu. Mitigace = CSP + žádný XSS + krátká session (později HttpOnly cookie s CSRF — větší změna).

---

### P2 — Střední

| ID | Nález | Stav |
|----|--------|------|
| P2-1 | Velký JSON body / image | **2mb** default + max image base64 + max text length |
| P2-2 | `rejectUnauthorized: false` u TLS inspect | **Zdokumentováno v kódu** — jen audit certu, ne proxy |
| P2-3 | Historie v `localStorage` | OK pro rodinu; zmíněno v Trust — UI warning později |
| P2-4 | Telefon syna v `localStorage` | Beze změny (lokální); rotace při prodeji tabletu |
| P2-5 | CI | **GitHub Actions** `.github/workflows/ci.yml` |
| P2-6 | Automatické testy | **`npm test`** — SSRF unit tests |
| P2-7 | `x-powered-by` | **Hotovo** (P0) |
| P2-8 | Timing-safe tokeny | **Hotovo** (P0) |

---

### P3 — Nízké / procesní

- Git větve: přijmout model **main (stable) / develop / feature/** (návrh z chatu) — až začneme pravidelné PR.
- Prompt Library (verzovaná) — po hybridní vrstvě.
- Režimy UI **Jednoduchý / Rozšířený / Analýza** místo Senior/Expert — produktově správně (Grok chat); zapsat do Design Principles.
- Rotace `ADMIN_TOKEN` / `FAMILY_CODE` / Gemini key po auditu jako hygiena.

---

## 4. Co je už dobře

- Gemini klíč **není** ve frontendu.
- `.env*` v gitignore; example bez reálných secretů.
- Admin endpointy vyžadují Bearer.
- History POST vyžaduje `familyCode`.
- Phishing pre-check před Gemini (kill-switch).
- Fallback když Gemini selže (nespadne úplně tiše).
- Cloudflare Tunnel = HTTPS pro PWA/mikrofon.
- Family DB runtime mimo git.

---

## 5. Plán nápravy (paralelní noha k Foundation)

| Pořadí | Úkol | Priorita |
|--------|------|----------|
| 1 | Opravit heartbeat (povinný family code) | P0 |
| 2 | Helmet + disable x-powered-by | P0 |
| 3 | Rate-limit (analyze, ssl, scam-alerts, family write) | P0 |
| 4 | SSRF guard na hostname/IP | P1 |
| 5 | Snížit body limit / limity image | P1 |
| 6 | Timing-safe admin compare | P2 |
| 7 | CI: lint + build + npm audit | P2 |
| 8 | Test: heartbeat bez kódu → 403 | P2 |
| 9 | Deploy na Lenovo + ověření hlaviček | po 1–3 |
| 10 | Design Principles + režimy UI (Foundation) | paralelní, nižší priorita než P0 |

---

## 6. Doporučení k Grok chatu (syntéza)

| Tvrzení | Náš verdikt |
|---------|-------------|
| Paralelní Foundation + security | **Přijato** (D-017) |
| Ne 3–4 týdny jen dokumenty | **Souhlas** |
| Repo neexistuje | **Opraveno** — existuje private |
| main/stable/develop | **Přijmout** při dalším dev workflow |
| Prompt Library | Až po hybrid + security základu |
| Režimy místo Senior/Expert | **Ano** — do Design Principles |

---

## 7. Opravy provedené 2026-07-30 (kód na Asus, deploy na Lenovo až po tvé kontrole)

| Nález | Stav v kódu `ShadowGuard-Shadvert` |
|-------|-------------------------------------|
| P0-1 Heartbeat bez kódu | **Opraveno** — bez platného FAMILY_CODE → 403; bez konfigurace → 503 |
| P0-2 Rate-limit | **Přidáno** — `/api/*` 200/15min; analyze/ssl/scam-alerts 40/15min (env override) |
| P0-3 Helmet + x-powered-by | **Přidáno** — helmet (CSP zatím vypnutá pro SPA, doladit později); `disable('x-powered-by')` |
| P2-1 Body limit | Sníženo default **2mb** (env `JSON_BODY_LIMIT`) |
| P2-8 Timing-safe compare | Admin token + family code přes `crypto.timingSafeEqual` |
| npm audit | **0 vulnerabilities** (po `npm install`) |

**Hotovo:** deploy P0 na Lenovo (2026-07-30) — zakladatel potvrdil **Deploy OK**.  
**Hotovo v kódu + Lenovo (SSRF):** P0 + P1-1 deploy OK.  
**Hotovo v kódu (další P1/P2):** cache scam-alerts, CSP+HSTS prod, limity image/text, CI, unit testy — **redeploy Lenovo**.  
**Odloženo (vědomě):** P1-3 per-device tokeny, P1-4 HttpOnly admin cookie (větší změna UX).

---

## 8. Deploy Lenovo — potvrzení

| Položka | Stav |
|---------|------|
| Pull + build + restart na Lenovo | **OK** (potvrzení zakladatele) |
| Live `shadowguard-shadvert.site` | běží s P0 kódem |
| Další P1 | SSRF guard, cache scam-alerts, silnější CSP |

---

## 9. Delta audit — 2026-08-06 (Trust Sprint)

**Účel:** ne audit z nuly, ale ověření, že P0 drží, a doplnění nálezů před closed betou (D-021).

### 9.1 Live re-check (`shadowguard-shadvert.site`)

| Kontrola | Výsledek 2026-07-30 | Delta 2026-08-06 |
|----------|---------------------|-----------------|
| HTTPS / CF | OK | OK |
| CSP | chybělo → pak helmet | **Ano** — `default-src 'self'`, `frame-ancestors 'none'`, `script-src 'self'` |
| HSTS | chybělo | **Ano** — `max-age=15552000` |
| X-Content-Type-Options | chybělo | **nosniff** |
| Referrer-Policy | chybělo | **no-referrer** |
| X-Frame-Options | chybělo | **SAMEORIGIN** (+ CSP frame-ancestors) |
| `GET /api/health` | OK | OK (`version` 1.0.0) |
| `POST /api/family/heartbeat` bez kódu | P0 bypass | **`403` Neplatný rodinný kód** ✓ |
| `POST /api/analyze-ad` `{}` | 400 | **400** ✓ |
| `npm audit` | 0 | **0** vulnerabilities |

### 9.2 Větev `ui/design-v2`

| Kontrola | Výsledek |
|----------|----------|
| Diff vs main | +SimpleResultCard, mapSimpleResult, sandbox `/design-v2`, docs, unit test mapování |
| Server / auth změny | **Žádné** — jen frontend + docs |
| Riziko pro live | Nízké, pokud se nenasadí jako default (D-019 / D-021: flag/closed) |
| CI na této větvi | **Ne** — workflow jen `main`/`develop` → P2: rozšířit branches |

### 9.3 Nové / přetrvávající nálezy (priorita)

| ID | Priorita | Nález | Doporučení |
|----|----------|--------|------------|
| D-P1-1 | P1 | AI verdikt bez `rulesVersion` / bez krátké cache → flapping (produktová důvěra) | Trust Engine MVP |
| D-P1-2 | P1 | Žádný React error boundary → bílý crash = ztráta důvěry seniora | Error boundary + srozumitelná hláška |
| D-P1-3 | P1 | Žádný automatický dad-path smoke skript | `scripts/smoke-beta.sh` |
| D-P2-1 | P2 | `url` / `userNote` v analyze-ad bez max length (jen rawText + image) | Cap např. url 2k, userNote 2k |
| D-P2-2 | P2 | CI neběží na `ui/design-v2` | Přidat branch pattern |
| D-P2-3 | P2 | `family/history` POST: při chybějícím FAMILY_CODE → 403 „neplatný kód“ (heartbeat má 503) | Sjednotit 503 |
| D-P2-4 | P2 | Admin token v sessionStorage (P1-4 z dřívějška) | Odloženo do >20 testerů / po CSP jistotě |
| D-P2-5 | P2 | Sdílený FAMILY_CODE (P1-3) | Odloženo — Beta Rule SGW-006 |
| D-P3-1 | P3 | Data inventory pro uživatele (soukromí „ukázat“) | Working + UI text |

### 9.4 Co delta **ne** otevřela znovu

- Heartbeat bypass — **zavřeno**  
- Rate-limit / helmet / SSRF / body limit / timing-safe — **drží**  
- Gemini klíč ve frontendu — **ne**  
- Secrets v gitu — **ne** (rychlý re-scan patternů OK)

### 9.5 Pořadí práce po deltě

1. D-P1-2 error boundary + D-P1-3 smoke  
2. D-P1-1 Trust Engine MVP (rulesVersion, golden hybrid, cache)  
3. D-P2-1 limity vstupů + D-P2-2 CI branches + D-P2-3 sjednocení family chyb  
4. Closed beta balíček (feedback 8 otázek)  
5. Jednoduchý režim jen pod flag (ne default main)

### 9.6 Opravy v kódu (Asus, 2026-08-06) — před deployem Lenovo

| ID | Stav v kódu |
|----|-------------|
| D-P1-1 | **Hotovo** — `RULES_VERSION`, `verdictSource`, in-memory verdict cache (TTL 10 min) |
| D-P1-2 | **Hotovo** — `ErrorBoundary.jsx` kolem App |
| D-P1-3 | **Hotovo** — `scripts/smoke-beta.sh` + `npm run smoke` (live PASSED) |
| D-P2-1 | **Hotovo** — max url 2k, userNote 2k |
| D-P2-2 | **Hotovo** — CI branches `ui/**`, `feature/**` |
| D-P2-3 | **Hotovo** — family/history bez FAMILY_CODE → 503 |
| Golden hybrid | **Hotovo** — `tests/phishingValidator.test.ts` (9 cases) |

**Deploy Lenovo:** ještě pull + build + restart (server.ts změny).  
**UI ErrorBoundary:** až po build/deploy frontendu.

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 1.0 | 2026-07-30 | První systematický audit kódu + live; P0–P3; plán nápravy |
| 1.1 | 2026-07-30 | Opravy P0 v kódu na Asus; čeká deploy na Lenovo |
| 1.2 | 2026-07-30 | Deploy Lenovo potvrzen zakladatelem (Deploy OK) |
| 1.3 | 2026-07-30 | P1-1 SSRF guard v kódu; čeká deploy Lenovo |
| 1.4 | 2026-07-30 | P1-2 cache alerts; CSP+HSTS; CI; tests; limity image/text |
| 1.5 | 2026-07-30 | P1/P2 + SSRF deploy OK na Lenovo; scam-alerts MISS-ERROR→HIT ověřeno; timeout 12s |
| 2.0 | 2026-08-06 | Delta Trust Sprint: live re-check P0 OK; D-P1/P2 tabulka; design-v2 scope |
