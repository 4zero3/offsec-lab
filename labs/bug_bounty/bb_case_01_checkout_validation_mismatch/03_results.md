# Results – Address Consistency Failure (Real Scenario_bug_bounty)

## Final Result

The case produced a clear and coherent result:

> The system did not enforce one authoritative address consistency state across the observed workflow.

Contradictory address data was not only accepted temporarily.

It was:

- accepted
- propagated
- persisted

---

## Core Finding

The strongest validated conclusion is:

> inconsistent billing-related address state can survive from address handling into final stored order data

This conclusion is not derived from a single observation.

It is derived from a complete workflow sequence.

---

## Result Chain

### 1. UI Validation Exists

The frontend performs validation.

Observed behavior:
- country / city mismatch indication
- generic address validation errors

This confirms:

> the system has defined expectations for address consistency

---

### 2. Validation Is Not Enforced Uniformly

A backend-supported address mutation accepted contradictory state.

Observed behavior:
- successful response
- inconsistent data accepted as valid state

Interpretation:

> validation is not centralized or authoritative

---

### 3. Preview Does Not Reconcile State

Checkout preview displayed contradictory address data.

Observed states:
- mismatched country/address combinations
- inconsistent invoice vs. delivery representation

Interpretation:

> preview does not normalize or reject inconsistent state

---

### 4. Workflow Continues to Completion

The checkout flow continued successfully.

Interpretation:

> no final consistency enforcement exists before order creation

---

### 5. Persistence Confirms the Failure

The inconsistent state was visible in:

- order overview
- order detail
- stored billing and delivery data

Interpretation:

> contradiction is not transient — it becomes persisted business data

---

## System Behavior Model

The observed behavior suggests a fragmented validation model:

- UI performs validation
- backend accepts conflicting state
- preview displays conflicting state
- checkout completes successfully
- persistence stores the conflicting state

This indicates the absence of a single authoritative validation boundary.

---

## What Was Proven

- address validation exists at UI level
- validation is not enforced consistently across workflow layers
- backend-supported mutation accepts inconsistent data
- checkout does not block or normalize the state
- inconsistent data is persisted in final order records

---

## What Was Not Proven

- no cross-user impact demonstrated
- no privilege escalation
- no payment manipulation
- no unauthorized data access
- no systemic abuse scenario validated

This case remains strictly within a single-user workflow integrity failure.

---

## Conclusion

The system does not enforce a consistent address state at persistence boundaries.

The decisive observation is not the presence of validation.

The decisive observation is:

> validation is not respected once the state enters backend-supported workflow transitions

---

## Core Insight

The decisive factor was not the form error.

The decisive factor was:

> backend acceptance → workflow continuation → persistence

---

## Key Learning

> A validation error only matters if the system enforces it at persistence boundaries.

In this case, it did not.