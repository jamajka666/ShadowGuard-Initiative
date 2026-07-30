# SGW-005 — Security Audit (Shadvert)

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGW-005 |
| **Title** | Security Audit — ShadowGuard Shadvert |
| **Version** | 1.0 |
| **Date** | 2026-07-30 |
| **Scope** | Live `shadowguard-shadvert.site` + kód `jamajka666/ShadowGuard-Shadvert` (private, clone na Asus) |
| **Status** | Findings — opravy v běhu / plánované |
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

**Náprava:** stejný rate-limit bucket; scam-alerts cacheovat (TTL).

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

| ID | Nález | Poznámka |
|----|--------|----------|
| P2-1 | `express.json` 10 MB | Snížit default; image zvlášť limitovat |
| P2-2 | `rejectUnauthorized: false` u TLS inspect | Pro audit certu záměrné, ale dokumentovat; nepoužívat pro „důvěřuj tomuto spoji“ |
| P2-3 | Historie kontrol v `localStorage` | Citlivé URL/texty na zařízení — OK pro rodinu, varovat v Trust/UI |
| P2-4 | Telefon syna v `localStorage` | `strazce_son_phone` — lokální, ale citlivé |
| P2-5 | Žádné CI (`npm audit` v Actions) | Zavést s lint/build |
| P2-6 | Žádné automatické testy security path | Minimálně test na heartbeat 403 |
| P2-7 | `x-powered-by: Express` | Fingerprinting |
| P2-8 | Timing-safe compare tokenů | `!==` na admin token — low risk u silného tokenu; ideálně `crypto.timingSafeEqual` |

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
**Hotovo v kódu:** SSRF guard P1-1 (`src/utils/ssrfGuard.ts`) — čeká `git pull` + build na Lenovo.  
**Ještě ne:** plná CSP, CI, doladění CSP pro SPA.

---

## 8. Deploy Lenovo — potvrzení

| Položka | Stav |
|---------|------|
| Pull + build + restart na Lenovo | **OK** (potvrzení zakladatele) |
| Live `shadowguard-shadvert.site` | běží s P0 kódem |
| Další P1 | SSRF guard, cache scam-alerts, silnější CSP |

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 1.0 | 2026-07-30 | První systematický audit kódu + live; P0–P3; plán nápravy |
| 1.1 | 2026-07-30 | Opravy P0 v kódu na Asus; čeká deploy na Lenovo |
| 1.2 | 2026-07-30 | Deploy Lenovo potvrzen zakladatelem (Deploy OK) |
| 1.3 | 2026-07-30 | P1-1 SSRF guard v kódu; čeká deploy Lenovo |
