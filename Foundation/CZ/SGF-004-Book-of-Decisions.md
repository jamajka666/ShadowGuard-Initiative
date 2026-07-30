# Book of Decisions

| Pole | Hodnota |
|------|---------|
| **Document ID** | SGF-004 |
| **Title** | Book of Decisions |
| **Edition** | Living Manuscript |
| **Version** | 1.0 |
| **Language** | Czech (CZ) |
| **Status** | Active |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 (D-010…D-014) |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert / celá iniciativa |

**Motto:** Rozhodnutí bez zápisu se ztrácí. Zápis bez důvodu je zbytečný.

---

## Účel

Tato kniha drží **trvalá a důležitá rozhodnutí**, aby se:

- neopakovala stejná debata dokola,
- neztratil kontext („proč jsme to tehdy udělali“),
- nová práce stavěla na jasných základech.

Není to deník (ten je Chronicle).  
Není to roadmapa (ta je Working).  
Je to **seznam rozhodnutí s odůvodněním**.

## Jak se rozhoduje

1. Pojmenovat problém.  
2. Vypsat **varianty** (pro / proti).  
3. Vybrat a zapsat sem.  
4. Teprve potom jednat ve velkém.

Malé technické detaily denní práce sem nepatří — jen to, co ovlivní směr na týdny a měsíce.

## Šablona zápisu

```
### D-XXX — Krátký název
- Datum:
- Status: accepted | superseded | deferred
- Kontext:
- Varianty:
- Rozhodnutí:
- Důvod:
- Důsledky:
```

---

## Rozhodnutí

### D-001 — Primární produkt je Shadvert

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Existuje veřejná app Shadvert i starší/domácí Python nástroj „ShadowGuard“ pro LAN. Hrozí zmatek, co je „ten pravý“ produkt. |
| **Varianty** | A) Rozvíjet oba stejně · B) Python jako hlavní · C) Shadvert jako produkt pro lidi, Python jako reference |
| **Rozhodnutí** | **C** — Shadvert (Node/React, shadowguard-shadvert.site) je primární produkt, který vidí rodina a budoucí uživatelé. Python rodinný engine zůstává **referencí a inkubátorem** logiky (heuristiky, RDAP, ntfy…), ne druhým konkurenčním produktem. |
| **Důvod** | Veřejná doména, PWA, rodinný sync a AI vysvětlení už běží v Shadvertu. Dvojí údržba „stejné věci“ by brzdila kvalitu. |
| **Důsledky** | Dokumentace a Foundation mluví o Shadvertu jako o první kapitole. Přenos dobrých pravidel z Pythonu do Shadvertu je vítaný; monorepo teď ne. |

---

### D-002 — Tempo práce bez zbytečného stresu

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Technické plány navrhovaly hustý 30denní sprint (15–20 h/týden). Zakladatel chce kvalitu, trpělivost a prostor vytvořit si vlastní úsudek z více názorů. |
| **Varianty** | A) Sprint 15–20 h/týden · B) 6–10 h · C) 8–12 h s bufferem |
| **Rozhodnutí** | **C** — orientačně **8–12 hodin týdně**, 2–4 sezení. Spěch není metrika úspěchu. |
| **Důvod** | Trpělivost nese růže. U senior produktu je horší unáhlená chyba než pomalejší milník. |
| **Důsledky** | Grokův technický obsah zůstává, časová osa se natahuje. Každé sezení má jeden jasný cíl a zápis do Chronicle. |

---

### D-003 — Freeze nových modulů do DoD Shadvert 1.0

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Vize ekosystému (další appky) je silná, ale bez jednoho spolehlivého jádra se rozpadne. |
| **Varianty** | A) Paralelně další produkty · B) Jen dokumentovat vizi · C) Freeze vývoje nových modulů, ekosystém jen v docs |
| **Rozhodnutí** | **C** — žádné nové produktové moduly (ShadowMail, hesla, …) dokud Shadvert neprojde Definition of Done 1.0 a closed betou. Ekosystém smí žít v dokumentaci a vizi. |
| **Důvod** | Jedna dokonalá věc > pět polotovarů. |
| **Důsledky** | Nápady na další appky → Working backlog. Priorita: bezpečnost, hybridní verdikt, senior UX, testeři. |

---

### D-004 — Dva stroje, žádný nepořádek

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Live verze Shadvertu běží na notebooku Lenovo. Nová práce a Foundation vznikají na Asus. |
| **Varianty** | A) Míchat obojí na jednom PC · B) Lenovo = stabilní online, Asus = vývoj a docs |
| **Rozhodnutí** | **B** — **Lenovo** drží současnou online verzi pro tátu. **Asus** je domov nové verze, Initiative repozitáře a systematické práce. |
| **Důvod** | Oddělení „co běží lidem“ od „co se právě staví“ snižuje riziko rozbití produkce a chaosu ve složkách. |
| **Důsledky** | Deploy změn na live až po vědomém rozhodnutí a kontrole. Archív AI konverzací zůstává v `~/ShadowGuard Initiative/` (mimo tento git, pokud není výslovně přidán). |

---

### D-005 — Současné bohaté UI je ukázka, ne konečný senior default

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Aktuální Shadvert má mnoho funkcí a komponent — záměrně i pro tátu jako ukázka „co to umí“. Hrozí přehlcení méně zvědavých seniorů. |
| **Varianty** | A) Okamžitě ořezat vše · B) Nechat jak je navždy · C) Zachovat schopnosti, ale budoucí výchozí cesta = minimální a jasná |
| **Rozhodnutí** | **C** — současná verze smí zůstat jako **ukázka / demo schopností**. Nová stabilizovaná verze bude mít **senior-first výchozí cestu** (vložit → ověřit → srozumitelný verdikt). Rozšířené prvky schovat pro syna/admin/„více“. |
| **Důvod** | Předvést se smí; mateřit se nesmí. |
| **Důsledky** | Při UX passi se komponenty třídí: Core / Rodina / Nice / Schovat v defaultu. Ne nutně mazat kód hned. |

---

### D-006 — Jazyky Foundation: CZ + EN + DE ve stejné verzi

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Official Language Editions. Otázka, zda vydávat foundation-v1.0 jen s CZ+EN. |
| **Varianty** | A) Jen CZ · B) CZ+EN, DE později · C) CZ+EN+DE najednou, pokud to nekomplikuje |
| **Rozhodnutí** | **C** — u klíčových manuskriptů **všechny tři jazyky ve stejné verzi**, pokud to nezpůsobí zmatek nebo zbytečné zpoždění. Překlad významu, ne doslov. |
| **Důvod** | Zakladatel žije v DE prostředí; EN je pro GitHub a budoucnost; CZ je jazyk myšlení. |
| **Důsledky** | SGF-003 v1.0 vyšel ve třech jazycích. Stejný přístup u Constitution a Way. |

---

### D-007 — Bezpečnost je cesta k důvěře (priorita č. 1 v technice)

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Audit i všechny AI shodně: klíče, rate-limit, tokeny, Helmet… |
| **Rozhodnutí** | Technická stabilizace začíná **bezpečností**. Bezpečnost není „nice-to-have“ — **vytváří důvěru**. |
| **Důvod** | Jeden únik klíče nebo zneužití API zničí příběh dřív než špatná barva tlačítka. |
| **Důsledky** | Sprint A (security) před feature polish. Hybridní detekce a prompty hned potom. |

---

### D-008 — Prompty jako kolektivní dílo (včetně Gemini)

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Verdikt appky stojí a padá s kvalitou promptů a hybridních pravidel. |
| **Rozhodnutí** | Prompty se tvoří a vylepšují **důkladně**, s pohledem více AI (včetně Gemini jako poskytovatele modelu) a s testovací sadou reálných příkladů. |
| **Důvod** | U seniorů je špatný verdikt horší než žádný nástroj. |
| **Důsledky** | Vznikne SGW-004 Prompt Library. AI je nástroj, ne absolutní soudce — pevná pravidla mají přednost u známých patternů. |

---

### D-009 — Ceremonie a slogany AI jsou vedlejší / k debatě

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Návrhy tisku, podpisu, silných sloganů. |
| **Rozhodnutí** | Ceremonie (tisk/podpis) je **vedlejší** a přijde až když text dává smysl. Sloganové formulace z ChatGPT se **neberou doslova** — jdou do debaty a zápisu, ne do slepé víry. |
| **Důvod** | Podstata > divadlo. Lidský cit pro „proč“ doplňuje techniku; dogmata ne. |
| **Důsledky** | `Foundation/Signed/` čeká. Motta v hlavičkách smí zůstat, pokud obstojí při opětovném čtení. |

---

### D-010 — Stabilní Document ID; pořadí čtení řeší Index

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Návrh přeuspořádat katalog (Manifesto = SGF-002, Way = SGF-003, …). Way a další už v gitu pod stávajícími ID. |
| **Varianty** | A) Přečíslovat vše · B) Stabilní ID + Foundation Index pro pořadí čtení |
| **Rozhodnutí** | **B** — jednou vydané SGF-ID se nemění. Manifesto = **SGF-006**. Decision Protocol = **SGF-009**. Index = **SGF-010**. Brand Identity rezervováno jako **SGF-011**. |
| **Důvod** | Stabilní odkazy, git historie, Time Capsule; přeuspořádání láme důvěru v dokumentaci. |
| **Důsledky** | Čtenář jde přes Foundation Index, ne podle „hezké“ posloupnosti čísel. |

---

### D-011 — Oficiální poradci + Decision Protocol (ne hlasování)

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Tři AI nemají být jen neformální chat; mají mít role. Návrh „hlasování“ by mohl vést k 2:1. |
| **Rozhodnutí** | Zavést **SGF-009 Decision Protocol**: Návrh → Analýza → Diskuse → Syntéza → Rozhodnutí zakladatele → Implementace → Validace. Role: ChatGPT strategický, Gemini produktový, Grok kritický; Grok Build = implementace; zakladatel vždy finále. **Žádné hlasování.** Námitky kdykoli vyslechnuty. |
| **Důvod** | Architektura rozhodování je stabilnější než demokracie modelů. |
| **Důsledky** | Velká rozhodnutí jdou protokolem; zápis do Book of Decisions / Chronicle. |

---

### D-012 — Názvy fází cesty (bez „Genesis“)

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Kódové jméno Genesis → asociace s filmem (Terminator Genisys), ne jen „vznik“. U brandu záleží na asociacích. |
| **Rozhodnutí** | Fáze: **Foundations → Direction → Craft → Trust → Launch → Growth**. Bez vojenského a prázdného startup tónu. CZ významy v Roadmap / Index. Později možné čistě české názvy, pokud sedí filozofii líp. |
| **Důvod** | Cesta > slogan. |
| **Důsledky** | SGW-002 Roadmap používá tyto názvy. |

---

### D-013 — Founding Edition release ještě ne

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Foundation už působí jako iniciativa; otázka okamžitého GitHub Release. |
| **Rozhodnutí** | **Počkat.** Nejdřív interní revize, konzistence jazyků, Brand Identity až bude ready, klidná kontrola Golden Rule. Release pojmenovat **Founding Edition v1.0** (ne jen „Foundation“). |
| **Důvod** | Release je slib oficiální filozofie. O pár kroků dřív než teď. |
| **Důsledky** | Práce na manuskriptech a Working pokračuje; tag/release až po revizi. |

---

### D-014 — Manifesto + PRINCIPLES.md + soukromý Founder Journal

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Potřeba jedné stránky „víry“ a krátkých pravidel pro nového čtenáře; deník „proč“ nemá být veřejný. |
| **Rozhodnutí** | **SGF-006 Manifesto** (CZ/EN/DE). Kořenový **PRINCIPLES.md** (10 pravidel). **Founder Journal** jen lokálně mimo veřejný git (`~/ShadowGuard Initiative/private/`). |
| **Důvod** | Veřejná filozofie vs. soukromá paměť zakladatele. |
| **Důsledky** | Journal se necommituje do ShadowGuard-Initiative. |

---

## Index

| ID | Název | Status |
|----|--------|--------|
| D-001 | Primární produkt Shadvert | accepted |
| D-002 | Tempo 8–12 h/týden | accepted |
| D-003 | Freeze modulů do DoD 1.0 | accepted |
| D-004 | Lenovo live / Asus vývoj | accepted |
| D-005 | Bohaté UI = ukázka; default senior-first | accepted |
| D-006 | CZ+EN+DE ve stejné verzi | accepted |
| D-007 | Security first | accepted |
| D-008 | Prompty kolektivně + hybrid | accepted |
| D-009 | Ceremonie vedlejší; slogany k debatě | accepted |
| D-010 | Stabilní Document ID + Index | accepted |
| D-011 | Decision Protocol (ne hlasování) | accepted |
| D-012 | Fáze cesty (bez Genesis) | accepted |
| D-013 | Founding Edition release ještě ne | accepted |
| D-014 | Manifesto, PRINCIPLES, Founder Journal | accepted |
| D-015 | Manifesto v1.1 (text); ID zůstává SGF-006 | accepted |

---

### D-015 — Manifesto v1.1 (obsah ano, přečíslování ne)

| | |
|--|--|
| **Datum** | 2026-07-30 |
| **Status** | accepted |
| **Kontext** | Review ChatGPT: Manifesto vyhovuje; návrhy na silnější úvod, větu o respektu/důvěře, podpis o začátku u jednoho člověka; znovu návrh posunout ID na SGF-002. |
| **Varianty** | A) Beze změny · B) Textové úpravy + držet SGF-006 · C) Text + přečíslovat celou knihovnu |
| **Rozhodnutí** | **B** — přijmout textové posílení (v1.1 ve CZ/EN/DE). **Nepřečíslovávat** (potvrzení D-010). Důležitost Manifestu vyjadřuje **pořadí čtení v Foundation Index** (hned po Founding Statement / vedle Constitution), ne číslo souboru. |
| **Důvod** | Text je podstata; stabilní ID chrání odkazy a historii. „Kapitoly jedné knihy“ = Index + tón, ne nutně 001–010 v ideálním pořadí. |
| **Důsledky** | Manifesto v1.1; katalog beze změny ID. |

---

## Revision Chronicle

| Revize | Datum | Změna |
|--------|-------|--------|
| 1.0 | 2026-07-30 | Založení knihy; rozhodnutí D-001 až D-009 z plánu a review zakladatele |
| 1.0 | 2026-07-30 | D-010 až D-014 — dodatky ChatGPT + shoda (Manifesto, Protocol, fáze, release wait) |
| 1.0 | 2026-07-30 | D-015 — Manifesto v1.1; potvrzení stabilních ID |
