# SGW-002 — Roadmap

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGW-002 |
| **Title** | Roadmap |
| **Version** | 0.2 |
| **Language** | Czech (CZ) |
| **Status** | Working draft |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-08-06 — Trust Sprint |

Working dokument — smí se měnit často.

---

## Fáze cesty (názvy)

Nepoužíváme kódová jména typu „Genesis“ (matoucí asociace).  
Fáze vyjadřují **cestu**:

| Fáze | Význam | Stav (orientačně) |
|------|--------|-------------------|
| **Foundations** | Budování základů — filozofie, protokoly, paměť | **většina hotová** (Founding Edition release ještě ne) |
| **Direction** | Směr a architektura (Architecture Truth, top 10) | čeká (po Trust craft) |
| **Craft** | Poctivá stavba Shadvertu (security → hybrid → UX) | **aktivní** — Trust Sprint 14 dní |
| **Trust** | Testování s prvními lidmi (rodina, známí) | **připravuje se** (táta + 5–10 closed) |
| **Launch** | První veřejnější vydání produktu | později |
| **Growth** | Rozvoj ekosystému | až po pevném jádru |

---

## Foundations — co zbývá před Founding Edition release

- [x] Constitution, Way (v1.1), Founding Statement  
- [x] Manifesto (v1.2), Decision Protocol, Foundation Index  
- [x] Book of Decisions, Chronicle (živě)  
- [x] **Trust Principles (SGF-008)** v1.0  
- [x] **Design Principles (SGF-007)** v1.0  
- [x] **SGW-006 Definition of Done**  
- [ ] Propsat režimy UI do Shadvert (Jednoduchý default)  
- [ ] CF Access na `/admin` (dashboard, ~15 min)  
- [ ] Brand Identity (SGF-011) — až bude připraveno  
- [ ] Interní revize všech Foundation textů (Golden Rule)  
- [ ] Konzistence terminologie CZ/EN/DE  
- [ ] Jednotná „titulní“ podoba Foundation Manuscript (později typografie/PDF)  
- [ ] **Teprve pak** GitHub Release **Founding Edition v1.0**  

Release **ještě ne**. Release = slib oficiální filozofie.  
**Architecture (Direction) až po Trust + Design Principles** — ať architektura čte hotovou filozofii.

---

## Direction (náhled — až po Trust/Design)

- SGW-003 Architecture Truth (Shadvert vs Python engine)  
- Inventura UI (Core / Nice / schovat v defaultu)  
- Security checklist  
- Top 10 priorit do Craft  

---

## Craft + Trust — Trust Sprint (14 dní od 2026-08-06)

Zdroj: ChatGPT produktový audit + plán Grok Build (korekce ID).  
Rozhodnutí: **D-021**. Gate: **SGW-007**.

| # | Priorita | Výstup |
|---|----------|--------|
| 1 | Delta security audit | SGW-005 revize (ne audit z nuly) |
| 2 | Opravy P0/P1 + stabilita dad-path | error boundary, smoke |
| 3 | Trust Engine MVP | rulesVersion, golden hybrid, verdict cache |
| 4 | Jednoduchý režim | **flag / closed**, ne hned default main (D-019) |
| 5 | Tester balíček | návod + 8 otázek (Google Form + lab) |
| 6 | Dokumenty | SGW-007, Chronicle — **ne** nové SGF-009 Trust Requirements |

**Feedback otázky (min.):** srozumitelnost · důvěra v „proč“ · ovládání · zmatek · jistota · **vzhled** · **doporučení** · **připomínky**.

**Mimo scope sprintu:** per-device enrollment, HttpOnly admin cookie, SGF-011 Brand, Founding Edition release, nové wow widgety v defaultu.

### Craft (náhled — po sprintu)

1. Security pass (klíče, Helmet, rate-limit, CI) — **základ hotov 2026-07-30**  
2. Hybridní verdikt + prompty — **rozšířit ve sprintu**  
3. Senior-first výchozí cesta — **po closed feedbacku**  
4. Testy + QA — golden + smoke  

---

## Tempo

8–12 h/týden · 2–4 sezení · jeden cíl na sezení · Decision Protocol u velkých voleb.

Řídící věta: **Nikdy neobětovat důvěru kvůli rychlosti.**

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 0.1 | 2026-07-30 | Draft: fáze cesty, Foundations checklist, náhled Direction/Craft |
| 0.2 | 2026-08-06 | Trust Sprint 14 dní; Craft/Trust aktivní; odkaz SGW-007 + D-021 |
