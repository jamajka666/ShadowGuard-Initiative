# SGW-007 — Feature Trust Gate

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGW-007 |
| **Title** | Feature Trust Gate |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Working (živý) |
| **Created** | 2026-08-06 |
| **Source** | ChatGPT audit (návrh „Trust Requirements“) + korekce Grok: **ne** SGF-009 (to je Decision Protocol) |
| **Navazuje na** | SGF-008 Trust Principles §VI, SGW-006 Definition of Done, SGF-001 pilíře |

Working dokument — smí se zpřesňovat. Nenahrazuje Foundation.

---

## 1. Účel

Každá **nová funkce** (nebo větší změna chování verdiktu / soukromí / výchozí UX) musí projít touto branou **před merge do produkční cesty** (main / live First Creation default).

> Pokud brána neprojde — funkce se nevydá.  
> Technicky zajímavé ≠ důvěryhodné.

**Nezaměňovat s SGF-009.**  
SGF-009 = Decision Protocol (jak se rozhodujeme).  
Tento dokument = produktový checklist důvěry u konkrétní funkce.

---

## 2. Checklist (povinný)

| # | Otázka | Ano? |
|---|--------|------|
| 1 | **Srozumitelná?** — člověk 70+ pochopí za pár sekund, co se děje? | ☐ |
| 2 | **Vysvětlitelná?** — je jasné *proč* verdikt / stav, a *co teď udělat*? | ☐ |
| 3 | **Bezpečná?** — žádné zbytečné riziko, secrets OK, relevantní P0/P1 z auditu? | ☐ |
| 4 | **Nezvyšuje zbytečně složitost?** — nepřidává obrazovky/žargon do defaultní cesty bez důvodu? | ☐ |
| 5 | **Respektuje soukromí?** — ukládá jen nutné; žádný skrytý sběr / prodej dat? | ☐ |
| 6 | **Nevyvolává falešný pocit jistoty?** — přiznává nejistotu; neslibuje víc, než umíme? | ☐ |

**Pravidlo:** pokud na kteroukoli otázku nelze říct poctivé **ano** — **ne merge do produkce**.

Doplňující (SGW-006 DoD): otestovaná, nasaditelná, zaznamenaná, v souladu s Foundation.

---

## 3. Kdy bránu použít

| Situace | Gate? |
|---------|--------|
| Hotfix, překlep, drobný CSS | Ne (stačí běžný review) |
| Security P0/P1 fix | Ano (body 3 + 5 + 6) |
| Změna verdiktu / skóre / semaforu | **Ano — všechny body** |
| Nová obrazovka / režim UI | **Ano** |
| Změna ukládání dat / family / AI payload | **Ano** |
| Experiment na větvi `ui/*` / lab | Gate až při **povýšení na default** |

---

## 4. Vztah k „Trust Engine“

Interní název pro hybridní vrstvu (pravidla → AI vysvětlení → fallback, `rulesVersion`, golden testy).

- Uživateli **neříkáme** „Trust Engine“.  
- Uživateli říkáme srozumitelně **proč** a **co teď**.  
- Gate bod 2 a 6 platí i pro AI texty.

---

## 5. Feedback closed bety (otázky pro testery)

Jednotný formulář (Google Form + lab export) — min. tyto otázky:

1. Bylo jasné, co výsledek znamená? (1–5)  
2. Věřil/a jste vysvětlení „proč“? (1–5)  
3. Bylo ovládání jednoduché? (1–5)  
4. Něco vás zmatlo? (volný text)  
5. Cítíte se po použití jistěji / stejně / nejistěji?  
6. **Který vzhled aplikace vám nejvíce vyhovoval?**  
7. **Doporučili byste tuto aplikaci?**  
8. **Připomínky** (volný text)

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 1.0 | 2026-08-06 | První verze — Trust Sprint; korekce ChatGPT SGF-009 → SGW-007 |
