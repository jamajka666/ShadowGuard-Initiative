# The ShadowGuard Way

| Field | Value |
|-------|--------|
| **Document ID** | SGF-002 |
| **Title** | The ShadowGuard Way |
| **Edition** | Founding Edition |
| **Version** | 1.0 |
| **Language** | English (EN) |
| **Status** | Official |
| **Created** | 2026-07-30 |
| **Last Revision** | 2026-07-30 |
| **Initiative** | ShadowGuard Initiative |
| **Project** | Shadvert / whole initiative |

**Motto:** Think slowly. Code only when the direction is clear. Never rush both at once.

---

## I. Purpose of this manuscript

The **Constitution (SGF-001)** states *why* we exist and *what* we stand for.  
**The ShadowGuard Way** states *how* we work day by day.

This is not a programming tutorial.  
It is an agreement on pace, quality, decisions, and collaboration — so the project lasts and stays true to the people it was built for.

---

## II. Relationship to other manuscripts

| Manuscript | Role |
|------------|------|
| SGF-001 Constitution | Why, values, founding question |
| SGF-002 The ShadowGuard Way | How we work (this document) |
| SGF-003 Founding Statement | Short heart of the story |
| SGF-004 Book of Decisions | Lasting decisions with reasons |
| SGF-005 Chronicle | What happened and why |
| SGF-006 Manifesto | One page of belief; trust over speed |
| SGF-009 Decision Protocol | How major decisions are made (not voting) |
| Working Library (SGW-*) | Sprints, architecture, prompts, backlog |

When the Way and daily reality drift apart, we **adjust the work or the decision** — we do not quietly break the rules.

---

## III. Four pillars in practice

The Constitution defines them. The Way turns them into habits:

| Pillar | In practice |
|--------|-------------|
| **Simplicity** | Senior path first; the rest only when the core is solid. Fewer screens, clearer words. |
| **Reliability** | Test odd inputs too. Prefer careful uncertainty over a false green light. |
| **Security** | Security first. Keys, tokens, rate limits, no secrets in git. Security builds trust. |
| **Trust** | Explainable verdicts. Honest disclaimers. Promise only what we can defend. |

**Founding question for every major change:**  
*Will this help someone feel safer online?*

---

## IV. Pace and rhythm

1. Roughly **8–12 hours per week**, typically **2–4 sessions**.  
2. Speed is **not** a success metric. Quality and calm are.  
3. Each session has **one main goal** and ends with a short Chronicle note (3–5 sentences is enough).  
4. Fatigue, life, work — **a pause is fine**. We write it down; we do not pretend.  
5. Better to **read three times** than skim once and ship something wrong.

Patience grows roses. A rushed verdict for a senior can grow harm.

---

## V. What a good session looks like

### Before work
- I know the session goal in one sentence.  
- I know whether I am touching Foundation, Working, or Shadvert code.  
- The live version on Lenovo does not change without a conscious decision (see D-004).

### During work
- I stay on the goal; new ideas go to the backlog, not the active branch.  
- For important decisions: options → pros/cons → write-down (Book of Decisions or at least Chronicle).  
- For code: each piece should be the best version of itself — **while keeping the pillars**, not at the cost of chaos elsewhere.

### After work
- Does what we set out to do work?  
- Did anything sensitive leak?  
- Chronicle (brief) and any decisions.  
- A clear “next step” for next time.

---

## VI. Decision-making

For **important** decisions, use the full **[SGF-009 Decision Protocol](../EN/SGF-009-Decision-Protocol.md)** (same folder in EN):

Proposal → Analysis → Discussion → Synthesis → **Founder’s decision** → Implementation → Validation.

In daily short form:

1. Name the problem.  
2. List **options** with pros and cons (advisors bring arguments, not votes).  
3. Synthesize a recommendation.  
4. **Founder decides** — AI advises; it does not decide.  
5. Record in **Book of Decisions** / Chronicle.  
6. Only then major action (Grok Build implements and tests; founder approves the record).

Small choices do not belong in the book.  
**No 2:1 voting** — arguments and the founder decide.

---

## VII. Working with AI and collective perspective

We take feedback from multiple sources seriously (ChatGPT, Grok, Gemini, people, testers).

Rules:

- **Good and bad** — we want both, so nothing surprises us.  
- Disagreement is written with a reason; blind agreement with every AI is not the goal.  
- Slogans and “ceremony” from chats are **proposals for debate**, not dogma.  
- **Prompts** are crafted and improved carefully (including Gemini’s perspective as the model), with a test set of real examples.  
- AI is a tool. Hybrid rules and verifiable facts take priority for known patterns.

The goal is not “do whatever AI says”.  
The goal is the **best possible version** of the idea with open eyes.

---

## VIII. Product quality and testing

1. We build for **ordinary people**, not for developers.  
2. We use the version that already works and improve it **step by step** — we do not rewrite everything overnight without reason.  
3. We also test **unlikely scenarios**, so we can stand behind the verdict.  
4. Definition of Done for a more public version includes real people (seniors / family / friends) — not only “it works on my machine”.  
5. The current rich UI may remain as a **capability showcase**; the default path for a less curious user should be **minimal and clear** (D-005).

Until the core is solid (security, reliable verdict, clarity), we **do not add new product modules** (D-003).

---

## IX. Code and engineering (working principles)

- **Security first** in every technical sprint (D-007).  
- No API keys, tokens, or passwords in git, in the frontend, or in screenshots.  
- Prefer clear, maintainable code over “clever” magic.  
- Production changes (live Lenovo) only after review — Asus is home for development and documentation.  
- Shadvert = product for people; Python engine = reference / logic incubator (D-001).  
- Every line of code should be the best version of itself — **while respecting the pillars and this Way**.

---

## X. Documenting the journey

We want the journey to be traceable:

| What | Where |
|------|--------|
| Why and values | Foundation (SGF-001…003) |
| Lasting decisions | SGF-004 Book of Decisions |
| What happened | SGF-005 Chronicle |
| How we build now | Working Library |
| Archive of AI discussions | with the founder (outside product git unless explicitly added) |

We document so we are not ashamed of chaos a year later — not so we write novels instead of working.

**Foundation manuscripts:** clear and short beats perfect forever.  
**Working manuscripts:** may change often.

---

## XI. Scope and backlog

- A new idea mid-session → **backlog**, not an instant detour.  
- An ecosystem of further apps may live in **vision and docs**; development only after Shadvert 1.0 DoD.  
- Feature creep is the enemy of a senior product. Freeze is not fear — it is discipline.

---

## XII. Languages and brand

- **CZ** — language where ideas are born.  
- **EN** — official international edition.  
- **DE** — Official Language Edition (founder’s environment).  
- Same version number across languages; translate **meaning**, not letters.  
- People see **Shadvert**. **ShadowGuard Initiative** remains the commitment in the background.

---

## XIII. What we deliberately do not do (now)

- We do not build a second app “because we can”.  
- We do not chase every external API in the world before the core works.  
- We do not treat ceremony (print, signature) as a gate for progress.  
- We do not promise absolute protection or a legal verdict.  
- We do not rush marketing before we hold up with real testers.

---

## XIV. Short checklist (keep it in your head)

Before merge / before “done”:

- [ ] Does this help the user’s safety or calm?  
- [ ] Is it clear to someone without an IT background?  
- [ ] Is it secure (keys, data, abuse)?  
- [ ] Can we explain the result?  
- [ ] Did we test an odd case too?  
- [ ] Is the decision / change written down when it matters?  
- [ ] Are we confusing live Lenovo with development Asus?

If you cannot answer one of these — **we are not done yet**.

---

## XV. Closing line

Good ideas are not ruined by patience.  
They are ruined by haste, confusion, and losing respect for the person on the other side of the screen.

The ShadowGuard Way is a reminder not to do that.

---

## Revision Chronicle

| Revision | Date | Change |
|----------|------|--------|
| Founding Edition 1.0 | 2026-07-30 | First official text — pace, decisions, AI, quality, code, documentation |
