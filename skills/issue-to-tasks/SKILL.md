---
name: issues-to-tasks
description: Break an issue file into concrete, ordered, AI-executable tasks. Use when the user wants to implement an issue, start work on a ticket, or break down an issue into smaller steps.
---

# Issues to Tasks

Break a single vertical-slice issue into concrete, ordered tasks that can each be completed in one focused AI session.

## Process

### 1. Locate the issue

Ask the user for the issue. If not provided, ask for the issue number or URL or file.
Read the parent PRD issue referenced in the "Parent PRD" field.

### 2. Explore the codebase

Explore the parts of the codebase touched by this issue. Focus on:

- Files and modules that will be created or modified
- Existing patterns to follow (naming conventions, error handling, test structure)
- Any interfaces or contracts this issue must respect

### 3. Draft the task list

Break the issue into ordered tasks. Each task must:

- Be completable in a single AI session (one focused prompt exchange)
- Have a clear, verifiable output (a file, a passing test, a working endpoint)
- Follow the dependency order: schema before logic, logic before API, API before UI, tests alongside or immediately after each layer

Label each task with its type:

- **WRITE**: create or modify production code
- **TEST**: write or update tests
- **MIGRATE**: schema or data migration
- **CONFIG**: environment, tooling, or infrastructure change
- **REVIEW**: human decision required before proceeding

Prefer WRITE and TEST tasks interleaved over a block of WRITE followed by a block of TEST.

### 4. Quiz the user

Present the proposed task list as a numbered list. For each task show:

- **Title**: short imperative description (e.g. "Add `user_id` column to `sessions` table")
- **Type**: WRITE / TEST / MIGRATE / CONFIG / REVIEW
- **Output**: what exists or passes when this task is done
- **Depends on**: task numbers that must complete first

Ask the user:

- Does the order feel right?
- Are any tasks too large to complete in one session?
- Are any tasks so small they should be merged?
- Are all REVIEW tasks correctly identified?

Iterate until the user approves the list.

### 5. Write the task file

Save the approved task list to a file in the format and location specified by the user.

Use the task file template below.

<task-file-template>
# Tasks for #<issue-number>: <issue-title>

Parent issue: #<issue-number>
Parent PRD: #<prd-issue-number>

## Tasks

### <n>. <Task title>

**Type**: WRITE / TEST / MIGRATE / CONFIG / REVIEW  
**Output**: <what exists or passes when done>  
**Depends on**: <task numbers or "none">

<A short paragraph describing exactly what to do. Written as an instruction to the AI that will execute it. Include: which files to touch, which pattern to follow, which existing code to use as reference. Do NOT include code snippets — describe intent, not implementation.>

---
</task-file-template>

Do NOT modify the parent issue or the parent PRD.
