# Evolution Principles

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGF-012 |
| **Title** | Evolution Principles |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Type** | ShadowGuard Foundation Manuscript |

**Motto:** Změna není cíl. Lepší zkušenost je cíl.  
**Motto 2:** Technologie slouží lidem, ne hardwaru.

---

## 1. Účel

Tento dokument říká, **jak se ShadowGuard Initiative smí a nesmí měnit v čase**.

Design Principles (SGF-007) říkají, jak má vypadat obrazovka.  
Trust Principles (SGF-008) říkají, jak se chováme k důvěře a datům.  
**Evolution Principles** říkají, jak přecházíme z generace na generaci — a co nikdy nesmíme obětovat rychlosti.

Vznikly i díky milníku **First Creation** (D-019): první živá verze není odpad, ale paměť.

---

## 2. Deset principů evoluce

### 1. Staré verze se nemažou
Významné generace produktu jdou do **Origin Gallery** (čestná galerie / archiv / demo), ne do koše.  
Učíme se z nich. Ukazujeme je. Respektujeme práci, ze které jsme vyšli.

### 2. Uživatel není pokusný králík
Živý default pro reálného člověka (např. tátu) se nepřepisuje tichým experimentem.  
Experimenty: větev, lab, opt-in, preview — ne překvapení pod rukama.

### 3. Nové funkce musí nejdřív získat důvěru
Funkce není „hotová“, dokud ji člověk pochopí a cítí se s ní jistěji — ne jen dokud prošla buildem.

### 4. Každá generace má být lepší — a pamatovat proč vznikla
Lepší ≠ víc widgetů. Lepší = srozumitelnější, bezpečnější, klidnější, poctivější.  
First Creation a další milníky drží odpověď na otázku *proč to vůbec děláme*.

### 5. Změna není cíl
Změna má sloužit zkušenosti a důvěře. Redesign bez důvodu je škodlivý.

### 6. Universal Accessibility — dlouhodobá kompatibilita
Technologie nesmí zbytečně vyřazovat lidi.

ShadowGuard usiluje o **co nejdelší podporu starších operačních systémů a zařízení** (včetně staršího Androidu a skromnějšího hardwaru), pokud to není v přímém rozporu s bezpečností.

Nové funkce **nesmí** být důvodem k nucené výměně telefonu nebo počítače.

> Pokud musíme ukončit podporu starší platformy, musí k tomu existovat **jasný bezpečnostní nebo technický důvod**, nikoli marketingový.

### 7. Respectful Interface — žádná otravná komerce na displeji
Rozhraní patří uživateli.

ShadowGuard **nebude** narušovat práci uživatele vyskakovacími reklamami, blikajícími bannery, agresivními marketingovými prvky, vnějším „pipáním“ ani partner-spamem.

**Obrazovka je pracovní prostor uživatele, nikoli reklamní plocha.**

*Důvěru nelze budovat rušením.*

**Výjimka (úzká):** vlastní oznámení jen když mají **přímou hodnotu pro bezpečnost nebo fungování** produktu — např. kritická oprava, vypršení tokenu, nutná bezpečnostní změna.  
**Nikdy:** „Kupte Premium“, akce, partneři, reklamní partneři třetích stran, bordel na displeji.

### 8. Calm Interface — každý prvek má důvod
Každý prvek na obrazovce musí pomáhat pochopit situaci nebo udělat správné rozhodnutí.  
Pokud nepomáhá, **nemá na obrazovce co dělat** (včetně zbytečných animací, pop-upů, badge a widgetů).

### 9. Technology serves people, not hardware
Lidé nemají měnit zařízení kvůli našemu softwaru. Pokud je to možné, **náš software se přizpůsobí jejich zařízení** — i telefonu, který běží šest sedm let.

### 10. Evoluce je pomalá v myšlenkách, rychlá jen v čistém kódu
*Kód budeme psát rychle jen tehdy, když budou myšlenky napsané pomalu.*  
Velké změny procházejí Decision Protocol (SGF-009) a Book of Decisions.

---

## 3. Origin Gallery (čestná galerie)

| Termín | Význam |
|--------|--------|
| **Origin Gallery** | Interní EN název pro trvalé místo / odkaz na významné generace (First Creation a další) |
| **Čestná galerie** | Český ekvivalent (ne „cestná“ — překlep) |
| **Účel** | Archiv, demo, inspirace, show-and-tell — ne smazání |

First Creation je první vklad do Origin Gallery, až přijde její čas na výstavku.

---

## 4. Lab a experimenty v čase

| Nyní (First Creation) | Později (možný růst) |
|------------------------|----------------------|
| **Design Lab** — vzorkovnice, dotazník | **Community Lab** — širší opt-in testy (texty, ikony, hlasy, režimy…) |
| Větve `ui/*`, `feature/*` | Volitelně i `prototype/*` pro nápady, které se nemusí nikdy mergnout |

Lab nikdy není povinný pro tátu. Data v labu: přednostně **lokálně** / export, ne skrytý tracking.

---

## 5. Role AI (pracovní mapa, ne hlasování)

| Role | Kdo | Účel |
|------|-----|------|
| Final Decision Authority | **Zakladatel** | Vždy finále |
| Chief Architect & Foundation Advisor | ChatGPT (strategie / Foundation) | Směr, struktura, principy |
| Strategic Reviewer & Devil’s Advocate | Grok | Kritika, rizika, poctivost |
| UX, Language & Human Communication | Gemini | Lidskost, jazyk, srozumitelnost |
| Lead Implementation Engineer | **Grok Build** (a další implementace) | Kód, deploy, větve |

**AI Council** = více pohledů před velkým rozhodnutím; **žádné hlasování** (viz SGF-009 / D-011).

Desktop / „Work“ aplikace stejného poskytovatele ≠ automaticky nová paměť: kontext drží **stejný účet a stejné vlákno** + Foundation dokumenty. Nový chat bez odkazů kontext ztrácí — proto existuje tato knihovna.

---

## 6. Kontrola před velkou změnou

Před nasazením nové generace na lidi, kteří nám důvěřují:

1. Je to lepší pro důvěru a srozumitelnost — ne jen „modernější“?  
2. Zůstává First Creation (nebo předchozí generace) v Origin Gallery?  
3. Funguje to na skromnějším / starším zařízení, pokud to bezpečnost dovolí?  
4. Ruší to uživatele reklamou nebo bordel na displeji? → **stop**.  
5. Je rozhodnutí zapsané (D-xxx)?

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 1.0 | 2026-07-30 | První vydání: evoluce, Universal Accessibility, Respectful + Calm Interface, Origin Gallery; vstup zakladatele + ChatGPT |
