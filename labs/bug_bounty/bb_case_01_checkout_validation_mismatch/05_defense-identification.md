# Defense Identification – Address Consistency Failure (Real Scenario_bug_bounty)

## Failed Control

The failed control in this case was:

> authoritative server-side enforcement of one coherent address state across workflow transitions

The system clearly expresses that address consistency matters.

That is visible through form-level validation behavior.

The failure is that this consistency requirement was not enforced uniformly once the state moved through backend-supported workflow layers.

---

## Why This Matters

A validation rule only has defensive value if it remains authoritative beyond the form.

In this case, the rule existed as visible expectation, but not as a consistently enforced workflow boundary.

That is the actual control failure.

The issue is therefore not:

- a missing label
- a cosmetic rendering problem
- a purely client-side inconsistency

It is a breakdown in how validity is decided and preserved across state transitions.

---

## Observable Failure Pattern

The following sequence was observed:

- the UI identified contradiction
- a backend-supported update accepted the contradiction
- preview displayed the contradiction
- completion did not stop the contradiction
- final order state preserved the contradiction

This pattern shows that the system did not rely on one final, authoritative consistency decision before persistence.

---

## Where the Model Breaks

The break did not occur at one field in isolation.

It occurred between multiple state layers:

- input validation
- backend-supported state mutation
- preview generation
- workflow completion
- persisted record generation

That makes the failure structural rather than superficial.

The problem is not simply that one field was accepted.

The problem is that contradictory state crossed multiple decision boundaries without being rejected or normalized.

---

## Nature of the Failure

This is a **state integrity failure**.

The application behaves as if different layers hold different standards for what counts as a valid address state.

That leads to a situation where contradiction is:

- visible to one layer
- tolerated by another
- preserved by the final workflow

This is exactly the kind of fragmentation that turns a weak validation issue into a real business-logic problem.

---

## Likely Defensive Weakness

The black-box evidence suggests one or more of the following weaknesses:

### 1. Validation authority is fragmented

The UI enforces one view of validity, but backend-supported workflow logic enforces another.

That means the frontend appears stricter than the state transition layer.

---

### 2. No final authoritative revalidation exists

If a contradiction reaches preview and still survives completion, then the workflow likely lacks a final authoritative consistency check before persistence.

---

### 3. Address components are not treated as one coherent object

Country, city, postcode, and street appear not to be evaluated as one unified state at every relevant boundary.

Instead, different parts of the workflow seem to evaluate only part of the whole.

---

### 4. Persistence trusts already-accepted state too much

Once contradictory state was accepted upstream, later stages behaved as if prior acceptance was sufficient.

That is dangerous, because workflow acceptance is not the same as true consistency.

---

## What the System Did Not Do

A robust control model would have done at least one of the following before final persistence:

- reject the contradictory state
- normalize it into one coherent state
- stop the workflow and require correction

The observed workflow did none of these reliably.

Instead, contradiction remained intact.

---

## Defensive Interpretation

The core defensive interpretation is:

> the system does not treat address consistency as one globally authoritative rule

It treats it as a partially enforced expectation.

That is why the contradiction was able to survive.

---

## Final Identification

The failed defense can be stated precisely as follows:

> The workflow did not enforce one authoritative server-side address consistency rule across input validation, backend-supported mutation, preview generation, completion, and final persistence.