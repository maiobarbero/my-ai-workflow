---
name: project-complexity-action-planner
description: >
  Convert a project complexity diagnosis into a practical intervention plan.
  Use after project-complexity-mapper, especially when the user provides a TOE
  findings table, quadrant chart, hotspot quadrants, management-fit table, or
  handoff table and wants actions, interventions, sequencing, owners, or next
  steps.
---

# Project Complexity Action Planner

Turn the output of `project-complexity-mapper` into a concise, actionable
management intervention plan. This skill does not diagnose complexity from
scratch. It consumes the previous diagnosis and turns it into actions.

## Core Workflow

1. Read the complexity diagnosis, especially the Handoff, Management Fit,
   Hotspot Quadrants, and Findings by Category sections.
2. Extract hotspots, TOE category, severity, quadrant, and recommended fit.
3. If key inputs are missing, infer cautiously and mark assumptions.
4. Ask at most one clarification question when the missing answer would change
   priority, sequencing, or ownership.
5. Convert each hotspot into controlling and/or connecting interventions.
6. Sequence actions by urgency, dependency, and lifecycle phase.
7. Output the plan using `references/output-format.md`.

## Input Rules

Preferred input is human-readable output from `project-complexity-mapper`.

Accept:

- Handoff table.
- Management Fit table.
- Findings by Category table.
- Mermaid quadrant chart plus short project description.
- Free-form summary of hotspots.

Do not require JSON, YAML, or machine-readable blocks.

If the user gives only a rough project description with no diagnosis, either:

- Ask them to run `project-complexity-mapper` first, or
- Do a very small provisional plan and clearly state that diagnosis is missing.

## Scope

In scope:

- Intervention backlog.
- Sequencing.
- Suggested owner roles.
- Time horizon.
- Control interventions.
- Connecting interventions.
- Decision gates.
- Reassessment triggers.
- Success signals.
- Risks of over-control or over-interaction.

Out of scope:

- Rebuilding the full TOE diagnosis.
- Creating detailed project schedule or Gantt chart.
- Writing tickets or implementation issues.
- Stakeholder interview questions.
- Machine-readable outputs.

## References

Load only what is needed:

- `references/handoff-input.md`: required when parsing previous diagnosis.
- `references/planning-rules.md`: required when prioritizing and sequencing.
- `references/intervention-catalog.md`: required when choosing interventions.
- `references/output-format.md`: required when writing final plan.

## Planning Principles

- Every action must trace back to a diagnosed hotspot.
- Prefer few high-leverage interventions over a long generic checklist.
- Match action type to quadrant:
  - Simple / Internal: keep simple.
  - Complicated: control.
  - Complex: connect.
  - Complex + complicated: combine control and connection.
- Sequence connecting work before control work when facts, goals, or actor
  positions are unstable.
- Sequence control work before broad interaction when interfaces, contracts, or
  technical dependencies must be made explicit first.
- Avoid false certainty. Mark assumptions and unresolved decisions.
- Include reassessment triggers because complexity evolves over the lifecycle.

## Output Rules

Use the structure in `references/output-format.md`.

Required sections:

1. Summary
2. Assumptions
3. Intervention Backlog
4. Sequence
5. Decision Gates And Reassessment
6. Risks In The Plan
7. Handoff

Do not include:

- Full TOE element checklist
- New quadrant diagnosis unless needed to explain an action
- Stakeholder-question section
- "What's Already Strong" section
- Machine-readable block
