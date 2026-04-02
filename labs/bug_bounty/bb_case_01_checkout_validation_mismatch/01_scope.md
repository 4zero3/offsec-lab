# Scope – Address Consistency Failure (Real Scenario_bug_bounty)

## Initial Situation

**Target Type:** authenticated e-commerce checkout workflow  
**Target:** private bug bounty target redacted

The objective was narrow.

The case did not attempt broad exploration of the platform.
It asked one question:

> Is one logically consistent address state enforced across address input, invoice update, checkout preview, order creation, and persisted order detail?

---

## Investigation Focus

The workflow was examined across these points:

- delivery address handling
- invoice address handling
- country / city / postcode / street consistency
- checkout preview state
- order persistence after successful completion

The core question was not whether the frontend shows an error.

The core question was:

> Does contradictory address state get rejected, normalized, or accepted by the system?

---

## Constraints

The investigation stayed within a normal authenticated user context.

Not tested:

- account takeover
- cross-user access
- payment fraud or price manipulation
- privilege escalation
- destructive automation
- large-scale fuzzing

Observations were derived from:

- normal browsing
- controlled checkout interaction
- traffic inspection
- validation of observed workflow behavior
- confirmation through visible workflow transitions

---

## Working Assumption

At the beginning, two interpretations were plausible:

1. the issue is only a frontend validation artifact.
2. the system accepts contradictory address state beyond the UI layer.

The case was built to distinguish between these two possibilities.

A UI error alone is weak.
A contradiction that survives workflow transitions is not.

---

## Success Condition

The case was only meaningful if the contradiction moved through multiple layers:

- contradictory address state introduced
- accepted by a backend-supported workflow
- visible in checkout preview
- order created successfully
- inconsistent state persisted in the final order record

Anything less would remain ambiguous.

---

## Final Scope Statement

This entry documents a business-logic validation issue concerning address consistency.

It does not identify the target publicly.

It documents one concrete black-box path where:

- validation was fragmented
- contradictory state was accepted
- checkout continued
- final business data preserved the inconsistency