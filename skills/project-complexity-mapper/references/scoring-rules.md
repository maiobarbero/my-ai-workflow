# Scoring Rules

Use these rules to score TOE elements, severity, impact, and confidence.

## TOE Contribution

Score how much the element contributes to project complexity.

| Score | Label | Meaning |
|---:|---|---|
| 1 | None | No meaningful contribution to project complexity |
| 2 | Little | Minor issue; unlikely to affect progress |
| 3 | Some | Noticeable complexity; should be monitored |
| 4 | Substantial | Important complexity; needs active management |
| 5 | Very much | Major complexity; likely to shape project approach |

## Detail Complexity

Score detail complexity from 1 to 5.

High detail indicators:

- Many components, work packages, requirements, contracts, locations, or actors.
- Strong dependencies between tasks or systems.
- Many technical or organizational interfaces.
- Multiple disciplines, standards, or methods.
- High need for decomposition, planning, or control.

Low detail indicators:

- Few parts.
- Few dependencies.
- Clear interfaces.
- Small team or narrow scope.
- Easy decomposition.

## Dynamic Complexity

Score dynamic complexity from 1 to 5.

High dynamic indicators:

- Scope, priorities, actors, or external conditions can change.
- Stakeholder positions are uncertain or unstable.
- Decision process is unpredictable.
- Political, regulatory, market, or social context is volatile.
- Methods, technology, or solution path are uncertain.
- Project phase changes which elements dominate.

Low dynamic indicators:

- Stable scope.
- Predictable decisions.
- Known technology.
- Low uncertainty.
- Stable stakeholders and environment.

## Impact

Impact means likely effect on project progress or value.

High impact if the element can affect:

- Schedule
- Cost
- Quality
- Safety
- Compliance
- Approval
- Trust
- Adoption
- Scope stability
- Delivery feasibility
- Value creation

Medium impact if the element matters but is contained by current practices.

Low impact if the element is present but unlikely to change project direction or
progress.

## Severity

Severity is based on TOE contribution plus impact on project progress.

| Severity | Rule |
|---|---|
| High | TOE 4-5 and high impact on progress, approval, trust, compliance, delivery feasibility, or value |
| Medium | TOE 3-4 with manageable impact, unclear mitigation, or moderate uncertainty |
| Low | TOE 1-3 with limited impact, or already well managed |

Do not use TOE score alone. A high TOE score can be Medium if impact is contained.
A moderate TOE score can be High if it threatens approval, trust, compliance, or
delivery feasibility.

## Confidence

| Confidence | Use When |
|---|---|
| High | User provided direct evidence; inference is straightforward |
| Medium | Evidence is partial but enough for a useful diagnosis |
| Low | Score depends on assumptions; ask a question if this affects top hotspots |

## Ranking

Rank hotspots by:

1. Severity
2. Impact
3. TOE contribution
4. Dynamic complexity
5. Confidence

Prefer surfacing uncertain high-impact elements over low-impact elements with
clean data.
