# My AI-Assisted Workflow

> How I built a structured AI-assisted development workflow as a Tech Lead, where the real work happens before a single line of code is written.

📖 **Full article:** [maiobarbero.dev/articles/ai-assisted-workflow](https://www.maiobarbero.dev/articles/ai-assisted-workflow/)

---

## The Problem

Vanilla AI-assisted coding feels fast — open a chat, describe what you want, ship something that works. But the speed comes at a cost: features that nobody fully understands, edge cases nobody thought to handle, and architecture that doesn't survive the next feature.

This workflow is the answer to one question: **how do you get the speed benefits of AI assistance without losing the clarity and intentionality that makes software maintainable?**

The short answer: the real work happens *before* the coding starts.

---

## Core Principle

AI is great at **implementation**. It's genuinely bad at figuring out what you actually want, catching implicit assumptions, and telling you when your mental model is wrong.

**That's your job. It will always be your job.**

Every step in this workflow shares the same structure:

> AI produces something → you review it with full context → it gets created.

The AI accelerates production. **The review is always yours.**

---

## The Workflow

```
Free-form Plan → PRD → Issues → Tasks → Code → Review → Final Audit
```

### Step 1 — Free-form Plan
Write a document in plain language. Describe the problem, your initial thinking, the constraints you're aware of, and the things you're uncertain about. No required structure. Nobody reads it but you. Its only job is to get the thinking out of your head.

> The quality of everything downstream depends entirely on the quality of this step.

### Step 2 — PRD (`write-a-prd`)
The free-form plan becomes the input to a structured interview. The skill explores the codebase, then interviews you about every aspect of the plan — walking down each branch of the design tree, resolving dependencies one by one.

The output is a structured **PRD** file containing:
- Problem statement & solution description
- Extensive user stories (the backbone of everything that follows)
- Implementation decisions (modules, interfaces, schema changes, API contracts)
- Module design & testing decisions
- Explicit out-of-scope items

### Step 3 — Issues (`prd-to-issues`)
The PRD becomes a set of issues using **vertical slices** — tracer bullets that cut through every integration layer end-to-end, never just a single layer.

Each issue is classified as:
- **AFK** — AI can implement and merge without human interaction
- **HITL** — a human decision is required at some point

Each issue contains: end-to-end behavior description, a "how to verify" section, acceptance criteria in Given/When/Then format (including error cases), blockers, and references to the user stories it addresses.

### Step 4 — Tasks (`issues-to-tasks`)
Each issue is broken down into concrete, ordered tasks — **one task per focused AI session**. If a task can't be completed in a single session, it's too large.

Task descriptions are written as **instructions to the AI that will execute them**, not as notes to a human. They specify which files to touch, which existing patterns to follow, and what done looks like.

Order follows: Schema → Logic → API → UI, with tests interleaved throughout.

### Step 5 — Handoff to Code
Each task description is a self-contained prompt. Open a fresh session, paste the task description plus the parent issue for context, and implement.

**Fresh context per task is intentional.** Long sessions drift — the model starts making decisions based on what it already did rather than what the task requires.

### Step 6 — Code Review (`code-review`)
Every PR goes through a structured six-pass review before merge:

1. Logic errors
2. Operation ordering
3. Bad practices
4. Security
5. Magic strings and values
6. Pattern improvements

> Pay particular attention to **operation ordering** — AI tends to do the right things in the wrong sequence (e.g. sending a notification before committing a transaction).

### Step 7 — Final Audit (`final-audit`)
A cross-cutting audit at the end of a feature, looking at things that can only be evaluated across the whole implementation: inconsistencies between modules, patterns replicated incorrectly, security assumptions that break down across the full surface area.

---

## What This Workflow Is Not

- **Not fast to set up.** Planning and PRD steps take real time. It pays off only if you genuinely believe thinking time before coding is cheaper than debugging time after.
- **Not a replacement for engineering judgment.** The AI will suggest reasonable things at every step that are wrong for your specific situation. Your review exists precisely because the AI lacks knowledge of your team's conventions, your users' actual behavior, and your codebase's hidden complexity.

---

## Credits

This workflow was adapted from Mark Pocock's [skills](https://github.com/mattpocock/skills/tree/main).

---

## Author

**Matteo "Maio" Barbero** — Software Engineer & Tech Lead

- 🌐 [maiobarbero.dev](https://www.maiobarbero.dev/)


*Tags: #AI #Workflow #TechLeadership #Productivity*
