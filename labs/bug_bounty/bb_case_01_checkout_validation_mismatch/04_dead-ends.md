# Dead Ends – Address Consistency Failure (Real Scenario_bug_bounty)

## Purpose

This section documents paths that were investigated and explicitly rejected.

A clean case is built by separating stable signal from weak artifacts.

---

## Dead End 1 – Pure Frontend Interpretation

The earliest signal was a form-level validation error.

This could have supported:

> the issue is only a frontend validation artifact

Rejected because the contradiction survived backend mutation, preview, and persistence.

---

## Dead End 2 – Single-Request Overinterpretation

A successful backend response was important, but not sufficient.

Rejected because one mutation was not enough.

The contradiction needed to survive the full workflow.

---

## Dead End 3 – Browser / Navigation Artifacts

Intermediate states were influenced by browser context or unstable navigation.

Rejected because they could not answer:

> what does the system accept and persist?

---

## Dead End 4 – Preview Alone as Final Proof

Preview is important, but preview alone is not the final decision boundary.

Rejected because a system may still reject at completion.

Persistence was required.

---

## Dead End 5 – Expanding Into Auth / Token Claims

Auth observations were noted but not merged.

Rejected because they do not strengthen the address consistency chain.

---

## Dead End 6 – Payment or Pricing Abuse

Checkout-adjacent behavior tempted broader impact claims.

Rejected because no validated pricing or payment manipulation was demonstrated.

---

## Final Dead-End Summary

Rejected interpretations:
- frontend-only issue
- single-request proof
- browser artifacts
- preview as final proof
- auth escalation
- payment abuse

The surviving case:
> contradictory address state was accepted, propagated, and persisted