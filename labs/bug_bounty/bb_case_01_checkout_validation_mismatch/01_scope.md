# Scope – Address Consistency Failure (Real Scenario_bug_bounty)

## Initial Situation

**Target Type:** authenticated e-commerce checkout workflow  
**Target:** private bug bounty target redacted

The objective was not broad exploration of a platform.

The objective was narrower:

> Determine whether one logically consistent address state is enforced across:
> - address input
> - invoice update
> - checkout preview
> - order creation
> - persisted order detail

---

## Investigation Focus

The case focused on the following areas:

- delivery address handling
- invoice address handling
- country / city / postcode / street consistency
- checkout preview state
- order persistence after successful flow completion

The central question was not whether the frontend shows an error.

The central question was:

> Does contradictory address state get rejected, normalized, or accepted by the system?

---

## Constraints

The investigation stayed inside a normal authenticated user context.

The following were **not** part of the tested scope:

- account takeover
- cross-user access
- payment fraud or price manipulation
- privilege escalation
- destructive automation
- large-scale fuzzing

All observations were derived from:

- normal browsing
- controlled checkout interaction
- traffic inspection
- validation of observed workflow behavior
- confirmation through visible workflow transitions

---

## Working Assumption

At the beginning, there were two plausible interpretations:

1. the issue is only a frontend validation artifact
2. the system accepts contradictory address state beyond the UI layer

The case was built to distinguish between these two possibilities.

That distinction mattered because a UI error alone is weak.

A persisted contradiction across workflow transitions is not.

---

## Target Surface

The practically relevant surface for this case included:

- checkout address forms
- invoice address editing behavior
- checkout preview
- finish / order completion flow
- order overview / order detail display

A particularly important workflow transition was the point where contradictory state stopped being a local form anomaly and became accepted application state.

> This transition became central because it marked the move from visible inconsistency to workflow-relevant state.

---

## Success Condition

This case would only count as meaningful if the contradiction could be shown to move through multiple layers.

The internal success condition was therefore:

- contradictory address state introduced
- accepted by backend-supported workflow
- visible in checkout preview
- order created successfully
- inconsistent state persisted in final order record

Anything less would remain ambiguous.

---

## Final Scope Statement

This entry documents a business-logic validation issue concerning address consistency.

It does **not** identify the target publicly.

It documents one concrete black-box path where:

- validation was fragmented
- contradictory state was accepted
- checkout transitions continued
- final business data preserved the inconsistency