# ShadowGuard Decision Protocol

| Field | Value |
|-------|--------|
| **Document ID** | SGF-009 |
| **Title** | ShadowGuard Decision Protocol |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | English (EN) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | whole initiative |

**Motto:** AI advises. The founder decides. The path of every decision is traceable.

---

## I. Purpose

This protocol describes **how important decisions are made** in the ShadowGuard Initiative.

It is not democracy of the form “two against one wins”.  
It is a **decision architecture**: arguments → synthesis → founder’s verdict → implementation → validation.

Small daily choices (variable names, tiny refactors) do not belong here.  
This is for decisions that change direction for days, weeks, or months.

---

## II. Roles

```
            ShadowGuard Initiative
                      │
                      ▼
          ┌───────────────────────┐
          │        Founder         │
          │  vision + final call   │
          └───────────┬───────────┘
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
   Strategic       Product         Critical
   advisor         advisor         advisor
  (ChatGPT)       (Gemini)         (Grok)
       └──────────────┼──────────────┘
                      ▼
           Decision Protocol (this document)
                      ▼
     Implementation & testing (Grok Build / local CLI)
                      ▼
           Founder approval (written record)
```

| Role | Who | Brings |
|------|-----|--------|
| **Founder** | human | direction, motivation, **final decision**, approval of the record |
| **Strategic advisor** | ChatGPT | architecture, UX, long-term strategy |
| **Product advisor** | Gemini | product, usability, structure, documentation |
| **Critical advisor** | Grok | weaknesses, alternatives, business/community angle, “what if not” |
| **Implementation** | Grok Build (local CLI) | build to approved instructions, checks, tests, change proposals |

**No advisor decides.**  
Each brings arguments.  
Decisions are always clearly traceable (Book of Decisions / Chronicle).

---

## III. Seven steps

### 1. Proposal
An idea, problem, or choice appears.

### 2. Analysis
Each relevant advisor (not always all three — depends on the topic) proposes a solution and **justifies** it.  
The founder may ask for explicit pros/cons and alternatives.

### 3. Discussion
Weaknesses, alternatives, risks, and surprises are examined.  
**Objections are welcome at any time** — they will be heard.  
This is not a vote. It is argument quality.

### 4. Synthesis
Arguments are compared. A **recommended solution** emerges (or two final candidates with a clear difference).

### 5. Founder’s decision
The founder weighs recommendations, may ask to confirm or refute specific points, and takes the **final decision**.  
Debate may reopen if a new fact appears.

### 6. Implementation
The approved brief goes to the implementation layer (typically Grok Build).  
Implementation:
- builds to requirements,
- checks and tests,
- comments and proposes changes,
- **does not finalize without founder approval**.

### 7. Validation
Result check, tests, possible adjustments.  
Lasting decisions → **Book of Decisions**.  
Journey → **Chronicle** (brief).

---

## IV. What this is not

| Wrong | Right |
|-------|--------|
| “Two AIs agree, one doesn’t → majority wins” | “Stronger argument and risk win — the founder decides” |
| Silent disagreement | Written objection with reason |
| “AI approved the merge” | Founder approved the record / deploy |

---

## V. Golden Rule for Foundation manuscripts

> **No Foundation manuscript is issued as an official Founding / closed edition until the founder (and advisors in review discussion) are convinced it captures the essence of the idea.**

Not “until everyone likes it”.  
But until it **really says what we mean to say**.

That is a large difference.

---

## VI. Links to other documents

| Document | Relationship |
|----------|----------------|
| SGF-002 The ShadowGuard Way | Daily habits and pace |
| SGF-004 Book of Decisions | Lasting decision log |
| SGF-005 Chronicle | Timeline memory |
| SGF-006 Manifesto | “Never sacrifice trust for speed” |
| Working Library | Sprints and technical implementation detail |

---

## VII. Checklist before closing a decision

- [ ] Is the problem named in one sentence?  
- [ ] Were at least two meaningful options considered (where it makes sense)?  
- [ ] Were critical / negative views raised?  
- [ ] Is the recommendation and why clear?  
- [ ] Did the founder decide explicitly?  
- [ ] Is there a Book of Decisions / Chronicle entry when it matters?  
- [ ] Does implementation know what it may and may not do without further approval?

---

## Revision Chronicle

| Revision | Date | Change |
|----------|------|--------|
| Founding Edition 1.0 | 2026-07-30 | Official protocol: 7 steps, advisor roles, no voting, Golden Rule |
