# Design Principles

| Feld | Wert |
|------|------|
| **Document ID** | SGF-007 |
| **Title** | Design Principles |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | German (DE) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert (erstes Produkt) |
| **Type** | ShadowGuard Foundation Manuscript |

**Motto:** Zuerst verständlich. Dann schön. Niemals beängstigend.

---

## 1. Zweck

Diese Prinzipien sagen, **wie jedes Produkt der ShadowGuard Initiative auf dem Bildschirm aussehen und sich verhalten soll**.

Sie sind keine ästhetischen Vorlieben.  
Sie sind Regeln, die Vertrauen schützen.

Jede UI-Entscheidung soll gegen dieses Dokument prüfbar sein.

**Design Rule 001:**  
*Der erste Bildschirm darf kein technisches Wissen voraussetzen.*

---

## 2. Drei Modi

Statt „Senior“ / „Expert“ nutzen wir drei Modi nach **Bedarf**, nicht nach Alter.

| Modus | Für wen | Zeigt | Standard |
|-------|---------|-------|----------|
| **Einfach** | Jeder, der schnell eine klare Antwort will | Ampel + kurze Erklärung + klarer Rat | **Ja** |
| **Erweitert** | Wer mehr Detail ohne Jargon will | Warum-Punkte + Verlauf + Alternativen | Nein |
| **Analyse** | Wer technische Grundlagen will | WHOIS, SSL, DNS, Scores, reichere Daten | Nein |

### Regeln der Modi

1. **Standard ist immer Einfach.** Keine Pflichtwahl beim ersten Start.  
2. Hochschalten ist möglich, nie Pflicht.  
3. Modus wird am Gerät gemerkt; zurück zu Einfach ist immer eine klare Geste.  
4. Im Modus Einfach **niemals** technische Details (IPs, Zertifikate, raw JSON…).  
5. Wir sagen nicht „In den Expertenmodus wechseln“.  
   Wir sagen: **„Mehr Details anzeigen“** (und „Technische Details“ für Analyse).

---

## 3. Zehn Designprinzipien

### 1. Zuerst verständlich
Jeder Bildschirm muss ohne Technikwissen funktionieren.  
Im Zweifel vereinfachen.

### 2. Erklären vor Warnen
Eine rote Warnung ohne Grund erzeugt Angst.  
Immer zuerst *warum*, dann *was tun*.

### 3. Ampel reicht nicht
Farbe ist nur Hilfe.  
Hauptsache ist ein kurzer Satz in Alltagssprache.

### 4. Keine Angstmacherei
Kein dramatisches Wording, unnötige Ausrufezeichen, aggressiver Ton.  
Ruhe > Drama.

### 5. Eine Hauptaktion
Jeder Bildschirm macht klar, was jetzt zu tun ist.  
Höchstens ein Primärbutton.

### 6. Groß und lesbar
Buttons mindestens **48×48 px**.  
Lesbare Schrift, hoher Kontrast, System-Textgröße respektieren.

### 7. Fehler sind nicht die Schuld des Nutzers
Bei Ausfall (Netz, KI, Timeout) ruhig erklären und nächsten Schritt anbieten.  
Nie nacktes „etwas ist schiefgelaufen“.

### 8. Privatsphäre ist sichtbar
Nutzer wissen, was gesendet wird und was auf dem Gerät bleibt.  
Keine stille Datensammlung.

### 9. Konsistenz vor Originalität
Gleiches sieht und verhält sich gleich.  
Keine Überraschungen nur um „interessant“ zu wirken.

### 10. Modus Einfach ist heilig
Nichts, was die Klarheit von Einfach stört, kommt in diesen Modus — auch wenn es „technisch besser“ wäre.

---

## 4. Sprache

- Klar, kurze Sätze.  
- Kein Jargon.  
- Menschliche Formulierungen statt Scores und Codes.  
- Ruhiger, erwachsener Ton.  
- Disclaimer ist Ehrlichkeit: Empfehlung, keine Garantie.

---

## 5. Visuelle Hierarchie (Modus Einfach)

1. **Ergebnis** — Ampel + ein starker Satz  
2. **Warum** — 2–4 kurze Punkte  
3. **Was jetzt tun** — klarer Rat  
4. Optional: **„Mehr Details anzeigen“** → Erweitert  

Nichts anderes auf dem ersten Ergebnisbildschirm.

---

## 6. Was wir absichtlich nicht tun

- Kein „Sind Sie Senior?“-Onboarding.  
- Keine Technikdetails im Einfach-Modus.  
- Keine Angst als Motivationsmittel.  
- Keine Gamification von Sicherheit.  
- Keine Deko-Animationen ohne Erklärungswert.  
- Keine Features, die den Hauptweg verwirren.

---

## 7. UI-Fertig-Filter

1. Im Einfach-Modus klar?  
2. Erklären vor Warnen?  
3. Hauptaktion offensichtlich?  
4. Im Einklang mit Trust Principles und Manifesto?  

Wenn irgendwo nein — Design zurück.

Vollständige Definition of Done: Working **SGW-006**.

---

## 8. Bezug zu anderen Manuskripten

| Dokument | Rolle |
|----------|--------|
| Manifesto | *warum* wir existieren |
| Trust Principles | *wie* wir Vertrauen bauen |
| The ShadowGuard Way | *wie* wir täglich arbeiten |
| **Design Principles** | *wie* es auf dem Bildschirm aussieht und sich verhält |

Dieses Dokument ist die praktische Brücke von Philosophie zum Produkt.

---

## Revision Chronicle

| Revision | Datum | Änderung |
|----------|-------|----------|
| Founding Edition 1.0 | 2026-07-30 | Offizielle Fassung aus ChatGPT + Grok + Gemini Konsens |
