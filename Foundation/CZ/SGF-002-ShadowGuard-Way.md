# The ShadowGuard Way

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGF-002 |
| **Title** | The ShadowGuard Way |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert / celá iniciativa |

**Motto:** Myšlenky pomalu. Kód až když je směr jasný. Nikdy obojí naráz ve spěchu.

---

## I. Účel tohoto manuskriptu

**Constitution (SGF-001)** říká *proč* existujeme a *čím* se řídíme.  
**The ShadowGuard Way** říká *jak* pracujeme den za dnem.

Toto není návod na programování.  
Je to dohoda o tempu, kvalitě, rozhodování a spolupráci — aby projekt vydržel a zůstal věrný lidem, pro které vznikl.

---

## II. Vztah k ostatním manuskriptům

| Manuskript | Role |
|------------|------|
| SGF-001 Constitution | Proč, hodnoty, zakládací otázka |
| SGF-002 The ShadowGuard Way | Jak pracujeme (tento dokument) |
| SGF-003 Founding Statement | Krátké srdce příběhu |
| SGF-004 Book of Decisions | Trvalá rozhodnutí s odůvodněním |
| SGF-005 Chronicle | Co se stalo a proč |
| Working Library (SGW-*) | Sprinty, architektura, prompty, backlog |

Když se Way a denní realita rozcházejí, **upravíme práci nebo rozhodnutí** — ne tiše porušujeme pravidla.

---

## III. Čtyři pilíře v praxi

Constitution je definuje. Way je převádí do návyků:

| Pilíř | V praxi to znamená |
|-------|---------------------|
| **Jednoduchost** | Nejdřív senior-cesta; zbytek až když je jádro jisté. Méně obrazovek, jasnější slova. |
| **Spolehlivost** | Testovat i „divné“ vstupy. Raději žlutá/nejistota než falešná zelená. |
| **Bezpečnost** | Security first. Klíče, tokeny, rate-limit, žádné tajemství v gitu. Bezpečnost tvoří důvěru. |
| **Důvěra** | Vysvětlitelný verdikt. Poctivý disclaimer. Slibujeme jen to, co umíme obhájit. |

**Zakládací otázka u každé větší změny:**  
*Pomůže to někomu cítit se na internetu bezpečněji?*

---

## IV. Tempo a rytmus

1. Orientačně **8–12 hodin týdně**, typicky **2–4 sezení**.  
2. Spěch **není** metrika úspěchu. Kvalita a klid ano.  
3. Každé sezení má **jeden hlavní cíl** a na konci krátký zápis do Chronicle (3–5 vět stačí).  
4. Unava, život, práce — **pauza je v pořádku**. Zapíše se, nic se netváří.  
5. Lepší **třikrát přečíst** než jednou prolistovat a spustit špatně.

Trpělivost nese růže. Unáhlený verdikt u seniora nese škody.

---

## V. Jak vypadá dobré sezení

### Před prací
- Vím, *co* je cíl sezení (jedna věta).  
- Vím, jestli sahám na Foundation, Working, nebo kód Shadvertu.  
- Live verze na Lenovo se nemění bez vědomého rozhodnutí (viz D-004).

### Během práce
- Držím se cíle; nové nápady jdou do backlogu, ne do rozjeté větve.  
- U důležitých rozhodnutí: varianty → pro/proti → zápis (Book of Decisions nebo aspoň Chronicle).  
- U kódu: každý kus má být co nejlepší verzí sebe — **při dodržení pilířů**, ne za cenu chaosu jinde.

### Po práci
- Funguje to, co mělo?  
- Neuniklo něco citlivého?  
- Chronicle (stručně) + případně rozhodnutí.  
- Jasný „další krok“ pro příště.

---

## VI. Rozhodování

1. Pojmenovat problém.  
2. Vypsat **dostupné varianty** a jejich pro / proti.  
3. Vybrat nejvhodnější — ne nutně nejdražší ani „nejchytřejší“.  
4. Velká rozhodnutí zapsat do **Book of Decisions**.  
5. Teprve pak velká akce.

Malé volby (název proměnné, drobný refaktor) do knihy nepatří.  
Směr na týdny a měsíce ano.

Výsledek rozhodnutí smí jít nejdřív k **diskuzi** (včetně více pohledů AI).  
Finální verdikt je **zakladatele** — AI radí, nerozhoduje.

---

## VII. Práce s AI a kolektivním pohledem

Bereme vážně připomínky z více zdrojů (ChatGPT, Grok, Gemini, lidé, testeři).

Pravidla:

- **Dobré i špatné** — chceme slyšet obojí, ať nás nic nepřekvapí.  
- Nesouhlas se zapisuje s důvodem; slepá shoda se všemi AI není cíl.  
- Slogany a „ceremonie“ z chatů bereme jako **návrhy k debatě**, ne dogmata.  
- **Prompty** tvoříme a vylepšujeme důkladně (včetně pohledu Gemini jako modelu), s testovací sadou reálných příkladů.  
- AI je nástroj. Hybridní pravidla a ověřitelná fakta mají u známých patternů přednost.

Cíl není „udělat co AI řekne“.  
Cíl je **nejlepší možná verze** nápadu s otevřenýma očima.

---

## VIII. Kvalita produktu a testování

1. Stavíme pro **běžné lidi**, ne pro vývojáře.  
2. Využíváme už hotovou verzi a **krok za krokem** ji zdokonalujeme — ne přepisujeme ze dne na den bez důvodu.  
3. Testujeme i **nepravděpodobné scénáře**, abychom si za verdiktem mohli stát.  
4. Definition of Done pro veřejnější verzi zahrnuje reálné lidi (senioři / rodina / známí) — ne jen „u mě to běží“.  
5. Současné bohaté UI smí zůstat jako **ukázka schopností**; výchozí cesta pro méně zvědavého uživatele má být **minimální a jasná** (D-005).

Dokud není hotové jádro (bezpečnost, spolehlivý verdikt, srozumitelnost), **nepřidáváme nové produktové moduly** (D-003).

---

## IX. Kód a technika (pracovní zásady)

- **Security first** v každém technickém sprintu (D-007).  
- Žádné API klíče, tokeny ani hesla v gitu, ve frontendu ani ve screencastech.  
- Preferovat srozumitelný, udržovatelný kód před „chytrou“ magií.  
- Změny na produkci (live Lenovo) jen po kontrole — Asus je domov vývoje a dokumentace.  
- Shadvert = produkt pro lidi; Python engine = reference / inkubátor logiky (D-001).  
- Každý řádek kódu by měl být nejlepší možnou verzí sebe — **za podmínky dodržení pilířů a tohoto Way**.

---

## X. Dokumentace průběhu

Kompletní průběh chceme mít dohledatelný:

| Co | Kam |
|----|-----|
| Proč a hodnoty | Foundation (SGF-001…003) |
| Trvalá rozhodnutí | SGF-004 Book of Decisions |
| Co se stalo | SGF-005 Chronicle |
| Jak teď stavíme | Working Library |
| Archív diskusí s AI | u zakladatele (mimo produktový git, pokud není výslovně přidán) |

Dokumentujeme proto, abychom se za rok nestyděli za chaos — ne proto, abychom psali romány místo práce.

**Founding manuskripty:** raději jasné a krátké než dokonalé na deset let bez tečky.  
**Working manuskripty:** smí se měnit často.

---

## XI. Scope a backlog

- Nový nápad uprostřed sezení → **backlog**, ne okamžitá odbočka.  
- Ekosystém dalších aplikací smí žít ve **vizi a dokumentaci**; vývoj až po DoD Shadvert 1.0.  
- Feature creep je nepřítel senior produktu. Freeze není strach — je to disciplína.

---

## XII. Jazyky a značka

- **CZ** — jazyk vzniku myšlenek.  
- **EN** — oficiální mezinárodní verze.  
- **DE** — Official Language Edition (prostředí zakladatele).  
- Stejné číslo verze napříč jazyky; překlad **významu**, ne písmen.  
- Lidé vidí **Shadvert**. **ShadowGuard Initiative** zůstává závazkem v pozadí.

---

## XIII. Co záměrně neděláme (teď)

- Nestavíme druhou appku „protože můžeme“.  
- Nehoníme všechny externí API světa, dokud nefunguje jádro.  
- Nebereme ceremonii (tisk, podpis) jako podmínku postupu.  
- Neslibujeme absolutní ochranu ani právní verdikt.  
- Nespěcháme do marketingu dřív, než obstojíme u reálných testerů.

---

## XIV. Krátký checklist (vytiskni si v hlavě)

Před merge / před „hotovo“:

- [ ] Pomáhá to bezpečí nebo klidu uživatele?  
- [ ] Je to srozumitelné člověku bez IT?  
- [ ] Je to bezpečné (klíče, data, zneužití)?  
- [ ] Umíme výsledek vysvětlit?  
- [ ] Otestovali jsme i divný případ?  
- [ ] Je rozhodnutí / změna někde zapsaná, když na tom záleží?  
- [ ] Nepleteme live Lenovo s vývojovým Asus?

Když na něco z toho nevíš odpověď — **ještě nejsme hotoví**.

---

## XV. Závěrečná věta

Dobré nápady se nekazí trpělivostí.  
Kazí se spěchem, zmatkem a ztrátou úcty k člověku na druhé straně obrazovky.

The ShadowGuard Way je připomínka, abychom to nedělali.

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| Founding Edition 1.0 | 2026-07-30 | První oficiální znění — tempo, rozhodování, AI, kvalita, kód, dokumentace |
