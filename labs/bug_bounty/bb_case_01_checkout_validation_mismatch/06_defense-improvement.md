# Defense Improvement – Address Consistency Failure

## Core Problem

Address validation is not enforced as one authoritative rule.

Different workflow layers apply different standards.

Result:

- contradiction is detected
- contradiction is accepted
- contradiction is propagated
- contradiction is persisted

---

## Required Model

Address state must be validated once by the backend as one coherent object and then carried unchanged through the workflow.

Country, postcode, city, and street must be evaluated together.

> If the state is inconsistent, the workflow must not continue.

---

## Required Controls

### 1. Central Validation Authority

Validation must be server-side and authoritative.

The UI may signal errors early, but it must not define validity.

### 2. Revalidation at Critical Boundaries

Validation must be enforced at:

- address update
- checkout preview
- order submission
- persistence

No stage may assume previous validation is sufficient.

### 3. Reject Contradictory State

If the address state is inconsistent, the system must reject it or block continuation until corrected.

No silent acceptance.

### 4. No Persistence of Invalid State

Contradictory state must never reach order creation or stored order data.

Persistence is the final integrity boundary.

### 5. No Trust in Previously Accepted State

Accepted once must not mean valid everywhere.

Each critical stage must revalidate.

### 6. Coherent Invoice / Delivery Logic

If invoice and delivery addresses both exist, each must be internally valid and their relationship must remain consistent.

---

## Core Insight

The decisive factor was not the form error.

> The decisive factor was backend acceptance, workflow continuation, and persistence.

---

## Key Learning

A validation error only matters if the system still respects it at persistence boundaries.

In this case, it did not.

---

## Final Statement

> Address consistency must be enforced as a backend-controlled invariant, not as a UI-level validation hint.