# ShadowGuard Decision Protocol

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGF-009 |
| **Title** | ShadowGuard Decision Protocol |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | celá iniciativa |

**Motto:** AI radí. Zakladatel rozhoduje. Cesta rozhodnutí je dohledatelná.

---

## I. Účel

Tento protokol popisuje, **jak vznikají důležitá rozhodnutí** v ShadowGuard Initiative.

Není to demokracie typu „2 proti 1 vyhrává“.  
Je to **architektura rozhodování**: argumenty → syntéza → finální verdikt zakladatele → realizace → kontrola.

Malé denní volby (název proměnné, drobný refaktor) sem nepatří.  
Sem patří rozhodnutí, která mění směr na dny, týdny nebo měsíce.

---

## II. Role v týmu

```
            ShadowGuard Initiative
                      │
                      ▼
          ┌───────────────────────┐
          │      Zakladatel        │
          │  vize + finální verdikt│
          └───────────┬───────────┘
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
  Strategický    Produktový     Kritický pohled
   poradce         poradce          poradce
  (ChatGPT)       (Gemini)          (Grok)
       └──────────────┼──────────────┘
                      ▼
           Decision Protocol (tento dokument)
                      ▼
     Implementace a testování (Grok Build / lokální CLI)
                      ▼
           Schválení zakladatelem (zápis)
```

| Role | Kdo | Přináší |
|------|-----|---------|
| **Zakladatel** | člověk | směr, motivace, **finální rozhodnutí**, schválení zápisu |
| **Strategický poradce** | ChatGPT | architektura, UX, dlouhodobá strategie |
| **Produktový poradce** | Gemini | produkt, použitelnost, struktura, dokumentace |
| **Kritický poradce** | Grok | slabiny, alternativy, obchodní a komunitní úhel, „co když ne“ |
| **Implementace** | Grok Build (lokální CLI) | realizace podle schválených instrukcí, kontrola, testy, návrhy úprav |

**Nikdo z poradců nerozhoduje.**  
Každý přináší argumenty.  
Rozhodnutí je vždy jednoznačně dohledatelné (Book of Decisions / Chronicle).

---

## III. Sedm kroků

### 1. Návrh
Vznikne nápad, problém nebo volba.

### 2. Analýza
Každý relevantní poradce (ne vždy všichni tři — podle tématu) navrhne řešení a **zdůvodní** ho.  
Zakladatel může požádat o explicitní pro / proti a varianty.

### 3. Diskuse
Hledají se slabiny, alternativy, rizika a nečekané komplikace.  
**Námitky jsou vítané kdykoli** — budou vyslechnuty.  
Nejde o „hlasování“. Jde o kvalitu argumentů.

### 4. Syntéza
Porovnají se argumenty. Vznikne **doporučené řešení** (případně 2 finální kandidáti s jasným rozdílem).

### 5. Rozhodnutí zakladatele
Zakladatel zhodnotí doporučení, případně nechá potvrdit nebo vyvrátit konkrétní body, a přijme **finální rozhodnutí**.  
Může kdykoli znovu otevřít debatu, pokud přibude nový fakt.

### 6. Implementace
Schválené zadání jde do implementační vrstvy (typicky Grok Build).  
Implementace:
- tvoří podle požadavků,
- kontroluje a testuje,
- komentuje a navrhuje změny,
- **nezapisuje finále bez schválení zakladatele**.

### 7. Validace
Kontrola výsledku, testy, případné úpravy.  
Trvalá rozhodnutí → **Book of Decisions**.  
Průběh → **Chronicle** (stručně).

---

## IV. Co není hlasování

| Špatně | Správně |
|--------|---------|
| „Dva AI souhlasí, jeden ne → vítězí většina“ | „Silnější argument a riziko vyhrává — rozhoduje zakladatel“ |
| Tichý nesouhlas | Zapsaná námitka s důvodem |
| AI „schválila merge“ | Zakladatel schválil zápis / deploy |

---

## V. Golden Rule pro Foundation manuskripty

> **Žádný Foundation Manuskript nebude vydán jako oficiální Founding / closed edition, dokud zakladatel (a při revizi i poradci v diskusi) nejsou přesvědčeni, že vystihuje podstatu myšlenky.**

Ne „dokud se všem líbí“.  
Ale dokud **opravdu říká to, co chceme říct**.

To je velký rozdíl.

---

## VI. Propojení s ostatními dokumenty

| Dokument | Vztah |
|----------|--------|
| SGF-002 The ShadowGuard Way | Denní návyky a tempo |
| SGF-004 Book of Decisions | Trvalý zápis rozhodnutí |
| SGF-005 Chronicle | Časová paměť |
| SGF-006 Manifesto | „Nikdy neobětovat důvěru kvůli rychlosti“ |
| Working Library | Sprinty, technické detaily implementace |

---

## VII. Checklist před uzavřením rozhodnutí

- [ ] Je problém pojmenovaný jednou větou?  
- [ ] Byly zváženy alespoň dvě smysluplné varianty (kde dává smysl)?  
- [ ] Padly i kritické / negativní pohledy?  
- [ ] Je jasné doporučení a proč?  
- [ ] Zakladatel výslovně rozhodl?  
- [ ] Je zápis v Book of Decisions / Chronicle, pokud na tom záleží?  
- [ ] Implementace ví, co smí a nesmí dělat bez dalšího schválení?

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| Founding Edition 1.0 | 2026-07-30 | Oficiální protokol: 7 kroků, role poradců, ne-hlasování, Golden Rule |
