---
name: prd-to-issues
description: Break a PRD into independently-grabbable issues using tracer-bullet vertical slices. Use when the user wants to convert a PRD to issues, create implementation tickets, or break down a PRD into work items.
---

# PRD to Issues

Break a PRD into independently-grabbable issues using vertical slices (tracer bullets).

## Process

### 1. Locate the files

Ask the user for the PRD file. Ask the user for the format, name, and location where the issue list should be saved.

### 2. Explore the codebase (optional)

If you have not already explored the codebase, do so to understand the current state of the implementation. Focus on the modules identified in the PRD's Module Design section.

### 3. Draft vertical slices

Break the PRD into **tracer bullet** issues. Each issue is a thin vertical slice that cuts through ALL integration layers end-to-end — schema, logic, API, UI, and tests — not a horizontal slice of a single layer.

Slices may be **HITL** or **AFK**:

- **HITL** (Human In The Loop): requires a human decision or review at some point during implementation — for example, an architectural decision, a design review, or approval of a schema migration
- **AFK** (Away From Keyboard): can be implemented and merged without human interaction

Prefer AFK over HITL wherever possible.

<vertical-slice-rules>
- Each slice delivers a narrow but complete path through every relevant layer
- A completed slice is demoable or independently verifiable
- Prefer many thin slices over few thick ones
- Slices that cannot be verified on their own are too coarse
</vertical-slice-rules>

### 4. Quiz the user

Present the proposed breakdown as a numbered list. For each slice show:

- **Title**: short descriptive name
- **Type**: HITL / AFK
- **Blocked by**: which other slices (if any) must complete first
- **User stories covered**: which numbered user stories from the PRD this addresses

Ask the user:

- Does the granularity feel right? (too coarse / too fine)
- Are the dependency relationships correct?
- Should any slices be merged or split further?
- Are all HITL slices correctly identified?

Flag any slice that addresses more than 2–3 user stories or would likely take more than half a day — it is probably too coarse and should be split.

Iterate until the user approves the breakdown.

### 5. Write the issue file

Write all approved issues to the file the user specified. Number issues sequentially and use those numbers for cross-references within the file.

Use the issue template below for each issue. Write issues in dependency order (blockers first).

Do NOT modify the PRD file.

<issue-template>
## Issue <n>: <title>

**Type**: HITL / AFK
**Blocked by**: Issue <n> / None — can start immediately

### Parent PRD

`<prd-filename>`

### What to build

A concise description of this vertical slice. Describe the end-to-end behaviour, not layer-by-layer implementation steps. Reference sections of the PRD rather than duplicating content.

### How to verify

Exactly how a developer (or the AI implementing this) confirms the slice is complete:

- **Manual**: step-by-step instructions to demo it
- **Automated**: what the test asserts

### Acceptance criteria

- [ ] Given <context>, when <action>, then <outcome>
- [ ] Given <failure condition>, then <expected behaviour>

### User stories addressed

- User story <n>: <short title>
- User story <n>: <short title>

---
</issue-template>
