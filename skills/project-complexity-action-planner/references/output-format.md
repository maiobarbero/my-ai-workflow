# Output Format

Use this structure for final intervention plan.

## Summary

Short overview:

- Input confidence.
- Number of hotspots converted into actions.
- Overall intervention posture.
- First 1-2 priorities.

Example:

```md
### Summary

Input confidence: Medium. Converted 3 hotspots into 6 interventions.
Overall posture: dynamic management, with control around interfaces and
connecting work around stakeholder alignment. First priority: stabilize legacy
integration dependencies before sprint commitments harden.
```

## Assumptions

List only assumptions that affect the plan.

```md
### Assumptions

| Assumption | Why It Matters |
|---|---|
| Municipality departments own source APIs | Changes owner and escalation path for integration work |
| Steering committee can make scope decisions | Needed to prevent stakeholder alignment from becoming endless discussion |
```

If no material assumptions exist, write: `No material assumptions beyond supplied diagnosis.`

## Intervention Backlog

Main table. Keep it traceable to the diagnosis.

```md
### Intervention Backlog

| Priority | Hotspot | Type | Action | Owner Role | Horizon | Success Signal | Risk If Ignored |
|---:|---|---|---|---|---|---|---|
| 1 | Legacy integrations | Mixed | Create interface register and run joint API prototype sessions for highest-risk systems | Integration lead | Now | Each critical API has owner, test endpoint, data contract, and escalation path | One integration blocks downstream modules and compresses testing |
| 2 | Stakeholder politics | Connecting + control gate | Align high-influence stakeholders on tradeoffs, then route scope decisions through steering committee | Project manager | Now | Concerns logged, decision rights clear, disputed scope has owner | Late objections create scope churn |
```

Type values:

- Control
- Connecting
- Mixed
- Keep simple

Horizon values:

- Now
- Next
- Later

## Sequence

Show why order matters.

```md
### Sequence

| Order | Do This | Before This | Reason |
|---:|---|---|---|
| 1 | Clarify API ownership and data contracts | Commit sprint scope | Avoid building against unstable integration assumptions |
| 2 | Align stakeholder tradeoffs | Freeze pilot scope | Prevent late political or departmental objections |
```

## Decision Gates And Reassessment

Keep concise.

```md
### Decision Gates And Reassessment

| Trigger | Review | Possible Decision |
|---|---|---|
| End of discovery | Re-score top hotspots | Continue, narrow scope, or add connecting work |
| Integration prototype fails | Review schedule and scope impact | Change integration approach or defer feature |
```

## Risks In The Plan

Name risks created by the recommended approach.

```md
### Risks In The Plan

| Risk | Why It Could Happen | Mitigation |
|---|---|---|
| Interaction delays decisions | Too many actors seek consensus | Use steering committee gate for final scope choices |
| Control artifacts drift from reality | API owners change or systems behave differently than documented | Pair interface register with live prototype reviews |
```

## Handoff

End with concise handoff for execution or another planning skill.

```md
### Handoff

| Priority | Action | Owner Role | Horizon | Depends On |
|---:|---|---|---|---|
| 1 | Create interface register and prototype critical APIs | Integration lead | Now | Department API owners identified |
| 2 | Run stakeholder tradeoff alignment and confirm decision rights | Project manager | Now | Sponsor confirms steering committee mandate |
```

## Do Not Include

- Full TOE diagnosis
- Stakeholder questions
- "What's Already Strong" section
- Machine-readable block
