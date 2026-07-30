# ShadowGuard Decision Protocol

| Feld | Wert |
|------|------|
| **Document ID** | SGF-009 |
| **Title** | ShadowGuard Decision Protocol |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | German (DE) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | gesamte Initiative |

**Motto:** KI berät. Der Gründer entscheidet. Der Weg jeder Entscheidung ist nachvollziehbar.

---

## I. Zweck

Dieses Protokoll beschreibt, **wie wichtige Entscheidungen** in der ShadowGuard Initiative entstehen.

Es ist keine Demokratie nach dem Muster „zwei gegen eins gewinnt“.  
Es ist eine **Entscheidungsarchitektur**: Argumente → Synthese → Urteil des Gründers → Umsetzung → Prüfung.

Kleine Alltagsentscheidungen (Variablennamen, winzige Refactors) gehören nicht hierher.  
Hierher gehören Entscheidungen, die die Richtung für Tage, Wochen oder Monate ändern.

---

## II. Rollen

```
            ShadowGuard Initiative
                      │
                      ▼
          ┌───────────────────────┐
          │        Gründer         │
          │  Vision + Endurteil    │
          └───────────┬───────────┘
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
  Strategischer   Produkt-        Kritischer
    Berater        berater          Berater
  (ChatGPT)       (Gemini)          (Grok)
       └──────────────┼──────────────┘
                      ▼
           Decision Protocol (dieses Dokument)
                      ▼
     Umsetzung & Tests (Grok Build / lokale CLI)
                      ▼
           Freigabe durch den Gründer (Niederschrift)
```

| Rolle | Wer | Bringt |
|-------|-----|--------|
| **Gründer** | Mensch | Richtung, Motivation, **Endentscheidung**, Freigabe der Niederschrift |
| **Strategischer Berater** | ChatGPT | Architektur, UX, langfristige Strategie |
| **Produktberater** | Gemini | Produkt, Nutzbarkeit, Struktur, Dokumentation |
| **Kritischer Berater** | Grok | Schwächen, Alternativen, Business-/Community-Winkel, „was wenn nicht“ |
| **Umsetzung** | Grok Build (lokale CLI) | Bau nach freigegebenen Anweisungen, Checks, Tests, Änderungsvorschläge |

**Kein Berater entscheidet.**  
Jeder bringt Argumente.  
Entscheidungen sind immer klar nachvollziehbar (Book of Decisions / Chronicle).

---

## III. Sieben Schritte

### 1. Vorschlag
Eine Idee, ein Problem oder eine Wahl entsteht.

### 2. Analyse
Jeder relevante Berater (nicht immer alle drei — je nach Thema) schlägt eine Lösung vor und **begründet** sie.  
Der Gründer kann explizit Pro/Contra und Varianten verlangen.

### 3. Diskussion
Schwächen, Alternativen, Risiken und Überraschungen werden geprüft.  
**Einwände sind jederzeit willkommen** — sie werden gehört.  
Es geht nicht um Abstimmung. Es geht um Qualität der Argumente.

### 4. Synthese
Argumente werden verglichen. Es entsteht eine **empfohlene Lösung** (oder zwei Endkandidaten mit klarem Unterschied).

### 5. Entscheidung des Gründers
Der Gründer wägt Empfehlungen ab, lässt ggf. Punkte bestätigen oder widerlegen, und trifft die **Endentscheidung**.  
Die Debatte kann wieder geöffnet werden, wenn neue Fakten hinzukommen.

### 6. Umsetzung
Das freigegebene Briefing geht an die Umsetzungsschicht (typisch Grok Build).  
Umsetzung:
- baut nach Anforderungen,
- prüft und testet,
- kommentiert und schlägt Änderungen vor,
- **schreibt nichts final ohne Freigabe des Gründers**.

### 7. Validierung
Ergebnisprüfung, Tests, ggf. Anpassungen.  
Dauerhafte Entscheidungen → **Book of Decisions**.  
Verlauf → **Chronicle** (kurz).

---

## IV. Was das nicht ist

| Falsch | Richtig |
|--------|---------|
| „Zwei KIs stimmen zu, eine nicht → Mehrheit gewinnt“ | „Stärkeres Argument und Risiko gewinnen — der Gründer entscheidet“ |
| Stiller Widerspruch | Schriftlicher Einwand mit Grund |
| „KI hat den Merge freigegeben“ | Gründer hat Niederschrift / Deploy freigegeben |

---

## V. Golden Rule für Foundation-Manuskripte

> **Kein Foundation-Manuskript wird als offizielle Founding / geschlossene Edition veröffentlicht, bis der Gründer (und Berater in der Review-Diskussion) überzeugt sind, dass es den Kern der Idee trifft.**

Nicht „bis es allen gefällt“.  
Sondern bis es **wirklich sagt, was wir sagen wollen**.

Das ist ein großer Unterschied.

---

## VI. Verbindung zu anderen Dokumenten

| Dokument | Beziehung |
|----------|-----------|
| SGF-002 The ShadowGuard Way | Tägliche Gewohnheiten und Tempo |
| SGF-004 Book of Decisions | Dauerhaftes Entscheidungsprotokoll |
| SGF-005 Chronicle | Zeitliche Erinnerung |
| SGF-006 Manifesto | „Vertrauen nie der Geschwindigkeit opfern“ |
| Working Library | Sprints und technische Umsetzungsdetails |

---

## VII. Checkliste vor dem Schließen einer Entscheidung

- [ ] Ist das Problem in einem Satz benannt?  
- [ ] Wurden mindestens zwei sinnvolle Varianten bedacht (wo es Sinn ergibt)?  
- [ ] Kam auch ein kritischer / negativer Blick vor?  
- [ ] Sind Empfehlung und Begründung klar?  
- [ ] Hat der Gründer ausdrücklich entschieden?  
- [ ] Gibt es einen Eintrag im Book of Decisions / Chronicle, wenn es darauf ankommt?  
- [ ] Weiß die Umsetzung, was sie ohne weitere Freigabe darf und nicht darf?

---

## Revision Chronicle

| Revision | Datum | Änderung |
|----------|-------|----------|
| Founding Edition 1.0 | 2026-07-30 | Offizielles Protokoll: 7 Schritte, Beraterrollen, keine Abstimmung, Golden Rule |
