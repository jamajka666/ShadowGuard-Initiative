# The ShadowGuard Way

| Feld | Wert |
|------|------|
| **Document ID** | SGF-002 |
| **Title** | The ShadowGuard Way |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | German (DE) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert / gesamte Initiative |

**Motto:** Gedanken langsam. Code erst, wenn die Richtung klar ist. Beides nie gleichzeitig in Eile.

---

## I. Zweck dieses Manuskripts

Die **Constitution (SGF-001)** sagt, *warum* wir existieren und *wonach* wir uns richten.  
**The ShadowGuard Way** sagt, *wie* wir Tag für Tag arbeiten.

Das ist keine Programmieranleitung.  
Es ist eine Vereinbarung über Tempo, Qualität, Entscheidungen und Zusammenarbeit — damit das Projekt hält und den Menschen treu bleibt, für die es entstand.

---

## II. Verhältnis zu anderen Manuskripten

| Manuskript | Rolle |
|------------|--------|
| SGF-001 Constitution | Warum, Werte, Gründungsfrage |
| SGF-002 The ShadowGuard Way | Wie wir arbeiten (dieses Dokument) |
| SGF-003 Founding Statement | Kurzes Herz der Geschichte |
| SGF-004 Book of Decisions | Dauerhafte Entscheidungen mit Begründung |
| SGF-005 Chronicle | Was geschah und warum |
| SGF-006 Manifesto | Eine Seite des Glaubens; Vertrauen vor Tempo |
| SGF-009 Decision Protocol | Wie wichtige Entscheidungen entstehen (keine Abstimmung) |
| Working Library (SGW-*) | Sprints, Architektur, Prompts, Backlog |

Wenn Way und Alltag auseinanderlaufen, **passen wir die Arbeit oder die Entscheidung an** — wir brechen Regeln nicht stillschweigend.

---

## III. Vier Säulen in der Praxis

Die Constitution definiert sie. Der Way macht daraus Gewohnheiten:

| Säule | In der Praxis |
|-------|----------------|
| **Einfachheit** | Senior-Pfad zuerst; der Rest erst, wenn der Kern steht. Weniger Bildschirme, klarere Worte. |
| **Zuverlässigkeit** | Auch „seltsame“ Eingaben testen. Lieber ehrliche Unsicherheit als falsches Grün. |
| **Sicherheit** | Security first. Schlüssel, Tokens, Rate-Limits, keine Geheimnisse in Git. Sicherheit schafft Vertrauen. |
| **Vertrauen** | Erklärbare Urteile. Ehrlicher Disclaimer. Nur versprechen, was wir vertreten können. |

**Gründungsfrage bei jeder größeren Änderung:**  
*Hilft das jemandem, sich im Internet sicherer zu fühlen?*

---

## IV. Tempo und Rhythmus

1. Etwa **8–12 Stunden pro Woche**, typisch **2–4 Sitzungen**.  
2. Eile ist **kein** Erfolgsmaß. Qualität und Ruhe sind es.  
3. Jede Sitzung hat **ein Hauptziel** und endet mit einem kurzen Chronicle-Eintrag (3–5 Sätze genügen).  
4. Müdigkeit, Leben, Arbeit — **Pause ist in Ordnung**. Wir schreiben sie auf; wir tun nicht so.  
5. Lieber **dreimal lesen** als einmal überfliegen und falsch ausliefern.

Geduld trägt Rosen. Ein überstürztes Urteil für einen Senior kann Schaden tragen.

---

## V. Wie eine gute Sitzung aussieht

### Vor der Arbeit
- Ich kenne das Sitzungsziel in einem Satz.  
- Ich weiß, ob ich Foundation, Working oder Shadvert-Code anfassen.  
- Die Live-Version auf dem Lenovo ändert sich nicht ohne bewusste Entscheidung (siehe D-004).

### Während der Arbeit
- Ich bleibe beim Ziel; neue Ideen gehen in den Backlog, nicht in den laufenden Branch.  
- Bei wichtigen Entscheidungen: Varianten → Pro/Contra → niederschreiben (Book of Decisions oder zumindest Chronicle).  
- Beim Code: jedes Stück soll die beste Version seiner selbst sein — **unter Einhaltung der Säulen**, nicht um den Preis von Chaos woanders.

### Nach der Arbeit
- Funktioniert, was funktionieren sollte?  
- Ist etwas Sensibles durchgerutscht?  
- Chronicle (kurz) und ggf. Entscheidung.  
- Klarer „nächster Schritt“ für das nächste Mal.

---

## VI. Entscheiden

Bei **wichtigen** Entscheidungen gilt das volle **[SGF-009 Decision Protocol](SGF-009-Decision-Protocol.md)**:

Vorschlag → Analyse → Diskussion → Synthese → **Entscheidung des Gründers** → Umsetzung → Validierung.

Kurz im Alltag:

1. Problem benennen.  
2. **Varianten** mit Pro/Contra (Berater bringen Argumente, keine Stimmen).  
3. Empfehlung synthetisieren.  
4. **Gründer entscheidet** — KI berät, entscheidet nicht.  
5. Eintrag ins **Book of Decisions** / Chronicle.  
6. Erst dann große Aktion (Grok Build setzt um und testet; Gründer gibt die Niederschrift frei).

Kleine Wahlen gehören nicht ins Buch.  
**Keine Abstimmung 2:1** — Argumente und der Gründer entscheiden.

---

## VII. Arbeit mit KI und kollektivem Blick

Wir nehmen Rückmeldungen aus mehreren Quellen ernst (ChatGPT, Grok, Gemini, Menschen, Tester).

Regeln:

- **Gutes und Schlechtes** — wir wollen beides, damit uns nichts überrascht.  
- Widerspruch wird mit Grund notiert; blinde Zustimmung zu jeder KI ist kein Ziel.  
- Slogans und „Zeremonie“ aus Chats sind **Vorschläge zur Debatte**, kein Dogma.  
- **Prompts** werden sorgfältig gebaut und verbessert (einschließlich Gemini als Modell), mit einer Testmenge realer Beispiele.  
- KI ist ein Werkzeug. Hybride Regeln und überprüfbare Fakten haben bei bekannten Mustern Vorrang.

Ziel ist nicht „tun, was die KI sagt“.  
Ziel ist die **bestmögliche Version** der Idee mit offenen Augen.

---

## VIII. Produktqualität und Tests

1. Wir bauen für **gewöhnliche Menschen**, nicht für Entwickler.  
2. Wir nutzen die bereits laufende Version und verbessern sie **Schritt für Schritt** — wir schreiben nicht ohne Grund über Nacht alles neu.  
3. Wir testen auch **unwahrscheinliche Szenarien**, damit wir hinter dem Urteil stehen können.  
4. Definition of Done für eine öffentlichere Version umfasst echte Menschen (Senioren / Familie / Freunde) — nicht nur „bei mir läuft es“.  
5. Die heutige reiche UI darf als **Fähigkeits-Demo** bleiben; der Standardweg für weniger neugierige Nutzer soll **minimal und klar** sein (D-005).

Solange der Kern nicht steht (Sicherheit, zuverlässiges Urteil, Verständlichkeit), **fügen wir keine neuen Produktmodule hinzu** (D-003).

---

## IX. Code und Technik (Arbeitsgrundsätze)

- **Security first** in jedem technischen Sprint (D-007).  
- Keine API-Schlüssel, Tokens oder Passwörter in Git, im Frontend oder in Screenshots.  
- Klarer, wartbarer Code vor „schlauer“ Magie.  
- Produktionsänderungen (Live Lenovo) nur nach Prüfung — Asus ist Zuhause für Entwicklung und Dokumentation.  
- Shadvert = Produkt für Menschen; Python-Engine = Referenz / Logik-Inkubator (D-001).  
- Jede Codezeile soll die bestmögliche Version ihrer selbst sein — **unter Einhaltung der Säulen und dieses Way**.

---

## X. Verlauf dokumentieren

Wir wollen den Verlauf nachvollziehbar halten:

| Was | Wohin |
|-----|--------|
| Warum und Werte | Foundation (SGF-001…003) |
| Dauerhafte Entscheidungen | SGF-004 Book of Decisions |
| Was geschah | SGF-005 Chronicle |
| Wie wir jetzt bauen | Working Library |
| Archiv der KI-Diskussionen | beim Gründer (außerhalb des Produkt-Gits, sofern nicht ausdrücklich aufgenommen) |

Wir dokumentieren, damit wir uns in einem Jahr nicht für Chaos schämen — nicht, um Romane statt Arbeit zu schreiben.

**Foundation-Manuskripte:** klar und kurz schlägt ewig perfekt.  
**Working-Manuskripte:** dürfen sich oft ändern.

---

## XI. Scope und Backlog

- Neue Idee mitten in der Sitzung → **Backlog**, kein sofortiger Abstecher.  
- Ein Ökosystem weiterer Apps darf in **Vision und Docs** leben; Entwicklung erst nach Shadvert-1.0-DoD.  
- Feature Creep ist der Feind eines Senior-Produkts. Freeze ist keine Angst — es ist Disziplin.

---

## XII. Sprachen und Marke

- **CZ** — Sprache, in der Gedanken entstehen.  
- **EN** — offizielle internationale Edition.  
- **DE** — Official Language Edition (Umfeld des Gründers).  
- Gleiche Versionsnummer über Sprachen; **Bedeutung** übersetzen, nicht Buchstaben.  
- Menschen sehen **Shadvert**. **ShadowGuard Initiative** bleibt die Verpflichtung im Hintergrund.

---

## XIII. Was wir absichtlich (jetzt) nicht tun

- Wir bauen keine zweite App „weil wir können“.  
- Wir jagen nicht alle externen APIs der Welt, bevor der Kern läuft.  
- Wir machen Zeremonie (Druck, Unterschrift) nicht zur Bedingung für Fortschritt.  
- Wir versprechen keinen absoluten Schutz und kein Rechtsverdikt.  
- Wir hetzen nicht ins Marketing, bevor wir bei echten Testern bestehen.

---

## XIV. Kurze Checkliste (im Kopf behalten)

Vor Merge / vor „fertig“:

- [ ] Hilft das der Sicherheit oder der Ruhe des Nutzers?  
- [ ] Ist es für jemanden ohne IT verständlich?  
- [ ] Ist es sicher (Schlüssel, Daten, Missbrauch)?  
- [ ] Können wir das Ergebnis erklären?  
- [ ] Haben wir auch einen seltsamen Fall getestet?  
- [ ] Ist die Entscheidung / Änderung festgehalten, wenn es darauf ankommt?  
- [ ] Verwechseln wir Live-Lenovo mit Entwicklungs-Asus?

Wenn du eine Antwort nicht weißt — **sind wir noch nicht fertig**.

---

## XV. Schlusssatz

Gute Ideen verderben nicht durch Geduld.  
Sie verderben durch Eile, Chaos und den Verlust des Respekts vor dem Menschen auf der anderen Seite des Bildschirms.

The ShadowGuard Way erinnert uns, das nicht zu tun.

---

## Revision Chronicle

| Revision | Datum | Änderung |
|----------|-------|----------|
| Founding Edition 1.0 | 2026-07-30 | Erste offizielle Fassung — Tempo, Entscheiden, KI, Qualität, Code, Dokumentation |
