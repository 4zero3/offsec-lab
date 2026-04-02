# Defense Identification – Address Consistency Failure (Real Scenario_bug_bounty)

## Failed Control

The failed control was:

> authoritative server-side enforcement of one coherent address state across workflow transitions

The system expresses that address consistency matters through form validation.

The failure is that this consistency requirement was not enforced once the state moved through backend-supported layers.

---

## Where the Model Breaks

The break occurred between multiple state layers:

- input validation
- backend-supported state mutation
- preview generation
- workflow completion
- persisted record generation

The problem is not one field.

The problem is contradictory state crossing decision boundaries without rejection or normalization.

---

## Likely Defensive Weakness

### 1. Validation authority is fragmented

UI enforces one view.
Backend-supported workflow enforces another.

---

### 2. No final authoritative revalidation

Contradiction reaches preview and survives completion.

No final consistency check before persistence.

---

### 3. Address components not evaluated as one object

Country, city, postcode, street not treated as unified state at every boundary.

---

### 4. Persistence trusts prior acceptance

Once accepted upstream, later stages assume prior acceptance is sufficient.

---

## What the System Did Not Do

A robust control would have done one of:

- rejected the contradictory state
- normalized it
- stopped the workflow

The observed workflow did none reliably.

---

## Defensive Interpretation

> the system does not treat address consistency as one globally authoritative rule

It treats it as a partially enforced expectation.

That is why the contradiction survived.