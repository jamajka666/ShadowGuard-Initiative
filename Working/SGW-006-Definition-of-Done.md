# SGW-006 — Definition of Done (+ Quality bar)

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGW-006 |
| **Title** | Definition of Done |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Working (živý) |
| **Created** | 2026-07-30 |
| **Source** | Shoda ChatGPT (DoD + Definition of Quality) + Grok + Gemini |

Working dokument — smí se zpřesňovat. Navazuje na Foundation, nenahrazuje ji.

---

## 1. Definition of Quality (5 bodů)

Produkt ShadowGuard je **kvalitní** pouze tehdy, pokud:

1. Je **bezpečný**.  
2. Je **srozumitelný**.  
3. Je **spolehlivý**.  
4. **Respektuje soukromí**.  
5. Dokáže **vysvětlit** svá doporučení.

> Kvalita není počet funkcí.  
> Kvalita je míra důvěry, kterou si produkt zaslouží.

---

## 2. Definition of Done — funkce / změna

Funkce nebo větší změna **není hotová**, dokud není:

| # | Kritérium | Odkaz |
|---|-----------|--------|
| 1 | **Bezpečná** (žádné zbytečné riziko, secrets OK, relevantní P0/P1 z auditu) | SGW-005, Trust |
| 2 | **Otestovaná** (automaticky a/nebo manuální smoke) | Way |
| 3 | **Srozumitelná** v režimu Jednoduchý | SGF-007 |
| 4 | **Vysvětlitelná** (proč + co teď udělat) | Trust, Design |
| 5 | **V souladu s Foundation** (4 pilíře, zakládací otázka) | SGF-001…009 |
| 6 | **Nasaditelná** (build, deploy checklist, rollback znám) | Deploy docs |
| 7 | **Zaznamenaná** (Chronicle / CHANGELOG / Issue dle dopadu) | Way |

Pokud chybí bod 1, 3 nebo 4 — **ne mergovat do produkce**.

---

## 3. Priority štítky (společný jazyk)

| Štítek | Význam |
|--------|--------|
| **P0** | Critical — bezpečnost / výpadek / ztráta důvěry |
| **P1** | Important — brzy, ale ne hasičák |
| **P2** | Improvement — zlepšení kvality |
| **P3** | Future — backlog, ne teď |

---

## 4. Beta Rule (FAMILY / enrollment)

- Do **úzké closed bety** (řádově do ~20 aktivních lidí, které známe): stačí silný **FAMILY_CODE** + možnost rotace.  
- **Jakmile aktivní testeři trvale překročí ~20** (nebo půjdeme mimo důvěryhodný okruh): automaticky vzniká úkol **per-device enrollment / tokeny** (P1).

---

## 5. Nejvyšší produktová otázka (po milnících)

> Opravdu se táta a dalších ~10 lidí cítí při používání Shadvertu **jistěji** než předtím?

To je důležitější milník než číslo verze.

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 1.0 | 2026-07-30 | DoD + Quality bar + P-štítky + Beta Rule z feedbacku AI |
