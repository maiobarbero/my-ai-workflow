# Handoff Input

Use this reference when reading output from `project-complexity-mapper`.

## Expected Sections

The previous skill may provide these sections:

- Summary
- Findings by Category
- Quadrant Matrix
- Overall Quadrant
- Hotspot Quadrants
- Complexity Map
- Management Fit
- Handoff

Prioritize inputs in this order:

1. Handoff table
2. Management Fit table
3. Hotspot Quadrants table
4. Findings by Category tables
5. Summary
6. Mermaid chart

## Minimum Useful Input

Minimum useful input contains:

- Element or hotspot name
- Severity or priority
- Quadrant or management fit

If TOE category, detail score, or dynamic score is missing, infer only if obvious.
Otherwise mark as unknown.

## Extraction Fields

Extract these fields when available:

| Field | Use |
|---|---|
| Priority | Initial ordering |
| Element | Action target |
| TOE | Type of complexity |
| Severity | Urgency and attention level |
| Score | Contribution to complexity |
| Detail | Need for control/decomposition |
| Dynamic | Need for interaction/adaptation |
| Quadrant | Management style |
| Recommended Fit | Intervention mix |
| Issue | Reason action is needed |
| Suggestion | Seed for action |
| Value Opportunity | Positive upside to preserve |

## Missing Diagnosis

If no real diagnosis is provided, do not pretend precision.

Use this sentence:

> I need the complexity diagnosis or handoff table from `project-complexity-mapper` to make this plan traceable. I can make a provisional plan from the project description, but confidence will be low.

Then ask whether to proceed provisionally or run diagnosis first.
