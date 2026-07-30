# Design Principles

| Field | Value |
|-------|--------|
| **Document ID** | SGF-007 |
| **Title** | Design Principles |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | English (EN) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert (first product) |
| **Type** | ShadowGuard Foundation Manuscript |

**Motto:** Understandable first. Beautiful second. Never frightening.

---

## 1. Purpose

These principles say **how every ShadowGuard Initiative product should look and behave** on screen.

They are not aesthetic preferences.  
They are rules that protect trust.

Every UI decision should be checkable against this document.

**Design Rule 001:**  
*The first screen must not assume technical knowledge.*

---

## 2. Three modes

Instead of “Senior” / “Expert” labels we use three modes by **need**, not by age.

| Mode | For whom | Shows | Default |
|------|----------|-------|---------|
| **Simple** | Anyone who wants a clear answer fast | Traffic light + short explanation + clear advice | **Yes** |
| **Extended** | Who wants more detail without jargon | Why-points + history + alternatives | No |
| **Analysis** | Who wants technical ground | WHOIS, SSL, DNS, scores, richer data | No |

### Mode rules

1. **Default is always Simple.** No forced choice at first launch.  
2. Moving up is optional, never required.  
3. Mode is remembered on device; return to Simple is always one clear gesture.  
4. Simple mode **never** shows technical details (IPs, certificates, raw JSON…).  
5. We do not say “Switch to Expert mode”.  
   We say: **“Show more details”** (and “Technical details” for Analysis).

---

## 3. Ten design principles

### 1. Understandable first
Every screen must work for someone with no technical background.  
When unsure, simplify.

### 2. Explain before you warn
A red warning without reason creates fear.  
Always *why* first, then *what to do*.

### 3. A traffic light is not enough
Colour is only a helper.  
The main thing is a short sentence in human language.

### 4. No fearmongering
No dramatic wording, unnecessary exclamation marks, or aggressive tone.  
Calm > drama.

### 5. One primary action
Every screen makes clear what to do now.  
At most one primary button.

### 6. Large and readable
Buttons at least **48×48 px**.  
Readable type, high contrast, respect system text scaling.

### 7. Errors are not the user’s fault
On failure (network, AI, timeout), explain calmly and offer a next step.  
Never bare “something went wrong”.

### 8. Privacy is visible
Users know what is sent and what stays on the device.  
No silent data collection.

### 9. Consistency over novelty
Same things look and behave the same.  
We do not surprise only to look “interesting”.

### 10. Simple mode is sacred
Nothing that hurts Simple-mode clarity enters that mode — even if it is “technically better”.

---

## 4. Language

- Clear, short sentences.  
- No jargon.  
- Prefer human phrasing over scores and codes.  
- Calm, adult tone.  
- Disclaimer is honesty: guidance, not a guarantee.

---

## 5. Visual hierarchy (Simple mode)

1. **Result** — light + one strong sentence  
2. **Why** — 2–4 short bullets  
3. **What to do now** — clear advice  
4. Optional: **“Show more details”** → Extended  

Nothing else on the first result screen.

---

## 6. What we deliberately do not do

- No “are you a senior?” onboarding.  
- No technical details in Simple mode.  
- No fear as a growth tool.  
- No gamification of safety.  
- No decorative motion that explains nothing.  
- No features that confuse the primary path.

---

## 7. UI done filter

1. Clear in Simple mode?  
2. Explain before warn?  
3. Primary action obvious?  
4. Aligned with Trust Principles and the Manifesto?  

If any answer is no — the design goes back.

Full Definition of Done: Working **SGW-006**.

---

## 8. Relation to other manuscripts

| Document | Role |
|----------|------|
| Manifesto | *why* we exist |
| Trust Principles | *how* we build trust |
| The ShadowGuard Way | *how* we work daily |
| **Design Principles** | *how* it looks and behaves on screen |

This document is the practical bridge from philosophy to product.

---

## Revision Chronicle

| Revision | Date | Change |
|----------|------|--------|
| Founding Edition 1.0 | 2026-07-30 | Official text from ChatGPT + Grok + Gemini consensus |
