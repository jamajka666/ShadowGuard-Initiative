# Design Principles

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGF-007 |
| **Title** | Design Principles |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert (první produkt) |
| **Type** | ShadowGuard Foundation Manuscript |

**Motto:** Nejdřív pochopitelné. Potom krásné. Nikdy strašidelné.

---

## 1. Účel

Tyto principy říkají, **jak má vypadat a chovat se** každý produkt ShadowGuard Initiative na obrazovce.

Nejsou to estetické preference.  
Jsou to pravidla, která chrání důvěru.

Každé UI rozhodnutí se má dát ověřit proti tomuto dokumentu.

**Design Rule 001:**  
*První obrazovka nesmí předpokládat technické znalosti.*

---

## 2. Triáda režimů

Místo nálepek „Senior“ / „Expert“ používáme tři režimy podle **potřeby**, ne podle věku.

| Režim | Pro koho | Co ukazuje | Výchozí |
|-------|----------|------------|---------|
| **Jednoduchý** | Každý, kdo chce rychlou a srozumitelnou odpověď | Semafor + krátké vysvětlení + jasná rada | **Ano** |
| **Rozšířený** | Kdo chce víc detailů, ale ne technický žargon | Body proč + historie + doporučené alternativy | Ne |
| **Analýza** | Kdo chce technické podklady | WHOIS, SSL, DNS, skóre, surovější data | Ne |

### Pravidla režimů

1. **Výchozí je vždy Jednoduchý.** Uživatel se nemusí rozhodovat při prvním spuštění.  
2. Přepnutí do vyššího režimu je možné, ale **není vyžadováno**.  
3. Režim se pamatuje na zařízení; návrat na Jednoduchý je vždy jedním jasným gestem.  
4. V režimu Jednoduchý **nikdy** neukazujeme technické detaily (IP, certifikáty, raw JSON…).  
5. Nepoužíváme formulaci „Přepnout do Expert režimu“.  
   Používáme: **„Zobrazit více podrobností“** (a případně „Technické podrobnosti“ pro Analýzu).

---

## 3. Deset designových principů

### 1. Nejdřív pochopitelné
Každá obrazovka musí být srozumitelná člověku bez technických znalostí.  
Když si nejsme jistí, zjednodušíme.

### 2. Vysvětli dřív, než varuješ
Červené varování bez vysvětlení budí strach.  
Vždy nejdřív *proč*, teprve potom *co s tím*.

### 3. Semafor nestačí
Barva (zelená / oranžová / červená) je jen pomůcka.  
Hlavní je krátká věta v lidské řeči.

### 4. Žádné strašení
Nepoužíváme dramatické formulace, zbytečné vykřičníky ani agresivní jazyk.  
Klíd > drama.

### 5. Jedna hlavní akce
Na každé obrazovce je jasné, co udělat teď.  
Maximálně jedno primární tlačítko.

### 6. Velké a čitelné
Tlačítka minimálně **48×48 px**.  
Dostatečná velikost písma, vysoký kontrast, respekt k systémovému zvětšení textu.

### 7. Chyba není vina uživatele
Při selhání (síť, AI, timeout) řekneme to klidně a nabídneme další krok.  
Nikdy holé „něco se pokazilo“.

### 8. Soukromí je vidět
Uživatel ví, co se posílá a co zůstává na zařízení.  
Žádné skryté sbírání dat.

### 9. Konzistence nad originalitou
Stejné věci vypadají a chovají se stejně.  
Nepřekvapujeme jen proto, abychom byli „zajímaví“.

### 10. Režim Jednoduchý je posvátný
Nic, co naruší srozumitelnost Jednoduchého režimu, se do něj nedostane — i kdyby to bylo „technicky lepší“.

---

## 4. Jazyk

- Česky (a Official Language Editions), srozumitelně, krátké věty.  
- Bez žargonu (API, token, endpoint, SSRF…).  
- Místo „validace selhala“ → „odkaz se nepodařilo ověřit“.  
- Místo „risk score 23“ → „vypadá to velmi podezřele“.  
- Oslovení klidné a dospělé — ne dětinské, ne úřednické.  
- Disclaimer (právní pojistka) je součástí poctivosti: doporučení, ne záruka.

---

## 5. Vizuální hierarchie (režim Jednoduchý)

1. **Výsledek** — semafor + jedna silná věta  
2. **Proč** — 2–4 krátké body  
3. **Co teď udělat** — jasná rada  
4. Volitelně: **„Zobrazit více podrobností“** → Rozšířený  

Nic jiného na první obrazovce výsledku.

---

## 6. Co záměrně neděláme

- Nenuíme výběr profilu / „jste senior?“ při startu.  
- Neukazujeme technické detaily v Jednoduchém režimu.  
- Nepoužíváme strach jako motivační nástroj.  
- Neděláme gamifikaci bezpečnosti.  
- Neplýtváme pozorností animacemi, které nic nevysvětlují.  
- Nepřidáváme funkce, které matou první cestu (feature creep).

---

## 7. Filtr před „hotovo“ (UI)

1. Je to srozumitelné v režimu Jednoduchý?  
2. Vysvětlujeme dřív, než varujeme?  
3. Je hlavní akce jasná?  
4. Je to v souladu s Trust Principles a Manifestem?  

Pokud na kteroukoli otázku „ne“ — návrh se vrací.

Úplná Definition of Done (bezpečnost, testy, dokumentace…): Working **SGW-006**.

---

## 8. Vztah k ostatním manuskriptům

| Dokument | Role |
|----------|------|
| Manifesto | *proč* existujeme |
| Trust Principles | *jak* budujeme důvěru |
| The ShadowGuard Way | *jak* pracujeme denně |
| **Design Principles** | *jak* to vypadá a chová se na obrazovce |
| PRINCIPLES.md | deset pravidel ve zkratce |

Tento dokument je praktický most mezi filozofií a produktem.

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| Founding Edition 1.0 | 2026-07-30 | Oficiální znění ze shody ChatGPT + Grok + Gemini + review zakladatele |
