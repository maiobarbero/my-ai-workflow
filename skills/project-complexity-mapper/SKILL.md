---
name: project-complexity-mapper
description: >
  Diagnose project complexity from a rough project description using the DelftX
  TOE framework and detail/dynamic complexity model. Use when the user wants to
  map, score, visualize, or understand project complexity; create a TOE matrix;
  generate a quadrant chart; or choose a fit-for-purpose management approach.
---

# Project Complexity Mapper

Turn a rough project description, project idea, or messy notes into a structured
complexity diagnosis. The output is a TOE assessment, overall and hotspot
quadrants, a Mermaid quadrant chart, and management-fit guidance.

This skill is diagnostic only. Do not create an action plan. End with a short
human-readable handoff table that another planning skill can use.

## Core Workflow

1. Read the user's project description.
2. Run a fast first-pass complexity scan by default.
3. Infer likely Technical, Organizational, and External complexity elements.
4. Ask only the few questions needed to resolve high-impact uncertainty.
5. Score relevant elements by TOE contribution, detail complexity, dynamic
   complexity, impact, severity, and confidence.
6. Output the report using `references/output-format.md`.
7. Include both overall project quadrant and per-hotspot quadrants.
8. Include a Mermaid quadrant chart for the main hotspots.
9. End with a human-readable handoff table.

## Assessment Modes

Default mode: Fast Complexity Scan.

- Use the user's free-form description as input.
- Infer likely TOE elements from the description.
- Ask only high-value clarification questions.
- Do not walk through all 47 TOE elements.
- Mark low-confidence scores clearly.

Complete mode: Full TOE Assessment.

- Before switching, ask the user if they want the complete 47-element assessment.
- Load `references/toe-elements.md`.
- Walk through all TOE elements.
- Score each element from 1 to 5.
- Separate user evidence from AI inference.
- Mark confidence for every score.

Use complete mode only when the user explicitly asks for it or agrees after being
asked.

## References

Load only what is needed:

- `references/output-format.md`: required when producing final report.
- `references/scoring-rules.md`: required when assigning scores, severity, and confidence.
- `references/management-approaches.md`: required when recommending management fit.
- `references/toe-elements.md`: required for complete 47-element assessment, optional for fast scan if element names are needed.

## Input Rules

Accept free-form project descriptions, rough thoughts, copied notes, or
partially structured text. Do not require JSON, YAML, templates, or forms.

Keep the interview light. Ask one question at a time only when the answer would
change the diagnosis materially.

Do not add a stakeholder-question section. It is fine to note that complexity is
subjective and should be reassessed with other perspectives, but do not generate
stakeholder interview questions.

## Complexity Principles

- Complexity is subjective: different actors can perceive the same project
  differently.
- Complexity evolves over the project lifecycle.
- TOE dimensions are Technical, Organizational, and External.
- Detail complexity means many parts, interfaces, dependencies, or disciplines.
- Dynamic complexity means uncertainty, change, limited predictability, shifting
  actors, or unstable context.
- Severity is based on TOE contribution plus impact on project progress.
- Do not flatten the project into one average. Preserve hotspots.
- The goal is fit-for-purpose management, not generic project management advice.

## Output Rules

Use the structure in `references/output-format.md`.

Required sections:

1. Summary
2. Findings by Category
3. Quadrant Matrix
4. Overall Quadrant
5. Hotspot Quadrants
6. Complexity Map
7. Management Fit
8. Handoff

Do not include:

- Action plan
- Stakeholder questions
- "What's Already Strong" section
- Machine-readable block
- JSON/YAML input or output mode
