---
name: code-review
description: Perform a language-agnostic first-pass code review covering
  logic errors, bad practices, operation ordering, magic strings, pattern
  improvements, strict type checking, and SQL injection. Use when asked to
  review code, audit a file, or check a diff. Accepts a single file, a diff
  with multiple hunks, or can explore the repo when needed to resolve
  external references. If no input is provided, ask the user to share a
  file or diff before proceeding.
---

# Code review

## Quick start

If the user has not provided a file or diff, ask:
> "Please share the code you'd like reviewed — paste it directly, upload a
> file, or provide a git diff."

This is a first-pass, language-agnostic review. It surfaces issues common
across all languages before any in-depth language-specific analysis.

## Input handling

| Input type | How to handle |
|------------|---------------|
| Single file | Review the full file |
| Git diff (one or more hunks) | Review changed lines and their surrounding context |
| Ambiguous reference (e.g. call to external method) | Explore the repo only as needed to verify whether the reference exists and what it does; do not read files unrelated to the finding |

## Review passes

Run all six passes on every review. Report findings grouped by severity.

### 1. Logic errors
- Infinite or unreachable loops (missing exit condition, invariant that
  never changes)
- Off-by-one errors in indices, ranges, or pagination
- Null / undefined dereferences that can crash at runtime
- Dead code that can never be reached
- Incorrect boolean logic (de Morgan violations, short-circuit mistakes)
- Race conditions or incorrect execution-order assumptions

### 2. Operation ordering
Flag sequences where order creates correctness or reliability risk:
- Side effects before guards (e.g. sending an email before committing a
  DB transaction, charging a card before persisting the order)
- Mutations or writes before validation of input
- Resource acquisition without matching release in all exit paths
  (locks, file handles, connections)
- Audit logging placed after the action it should record

### 3. Bad practices
- Raw request / user input used without sanitisation or validation
- Overly broad exception handling that silently swallows errors
- Missing error handling on I/O, network, or DB calls
- Unsafe type coercion or implicit casting between incompatible types
- Strict equality not enforced where type safety matters
  (e.g. `==` instead of `===` in JS/TS, or comparing values of
  different types without explicit conversion)
- Functions with hidden side effects or unclear single responsibility

### 4. Security
- SQL injection: string concatenation or interpolation used to build
  queries instead of parameterised queries / prepared statements
- Hardcoded secrets, credentials, tokens, or environment-specific values
- Exposed sensitive data in logs, error messages, or API responses

### 5. Magic strings and values
- Unnamed string or numeric literals used inline instead of named
  constants (e.g. `status === "active"`, `retries > 3`, `role === "admin"`)
- Duplicated literals that should share a single source of truth
- Suggest extracting to a constant, enum, or config value with a
  descriptive name

### 6. Pattern improvements
Flag cases where a well-known pattern would meaningfully reduce coupling,
improve testability, or clarify intent. Suggest only when the improvement
is concrete and actionable — do not suggest patterns for their own sake:
- Hard-coded dependencies that could use dependency injection (class
  instantiates its own collaborators, making unit testing difficult)
- Repeated conditional chains that could be replaced with a strategy or
  map lookup
- Procedural code that obscures a domain concept a named abstraction
  would clarify
- When exploring the repo reveals that a dependency is always used in the
  same way, note if a factory or builder would remove duplication

## Output format

For each finding:
- **Location** — file name and line number, or function / block if
  unavailable
- **Severity** — critical / high / medium / low
- **Pass** — which of the six passes caught it
- **Description** — what the problem is and why it matters
- **Fix** — a corrected snippet or concrete actionable suggestion

Group all findings by severity (critical first). End with a short summary
of overall quality and the top 1–3 issues to address immediately.

## Severity guide

| Severity | Meaning |
|----------|---------|
| Critical | Data loss, security breach, or crash in production |
| High     | Likely bug or incorrect behaviour under normal use |
| Medium   | Subtle risk or meaningful maintainability concern |
| Low      | Best-practice deviation with minor practical impact |

