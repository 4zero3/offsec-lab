# Defense Improvement – Address Consistency Failure

## Core Problem

Address validation is not enforced as one authoritative rule.

Different workflow layers apply different standards.

Result:
- contradiction detected
- contradiction accepted
- contradiction propagated
- contradiction persisted

---

## Required Model

Address state must be validated once by the backend as one coherent object and carried unchanged.

Country, postcode, city, street evaluated together.

> If inconsistent, workflow does not continue.

---

## Required Controls

### 1. Central Validation Authority

Server-side, authoritative.

UI signals early, does not define validity.

### 2. Revalidation at Critical Boundaries

Enforce at:
- address update
- checkout preview
- order submission
- persistence

No stage assumes prior validation is sufficient.

### 3. Reject Contradictory State

If inconsistent, reject or block until corrected.

No silent acceptance.

### 4. No Persistence of Invalid State

Contradictory state never reaches order creation or stored data.

Persistence is the final integrity boundary.

### 5. No Trust in Previously Accepted State

Each critical stage revalidates.

### 6. Coherent Invoice / Delivery Logic

Invoice and delivery addresses both internally valid and relationally consistent.

---

## Core Insight

The decisive factor was not the form error.

> The decisive factor was backend acceptance → workflow continuation → persistence.

---

## Key Learning

Validation only matters if enforced at persistence boundaries.

In this case, it was not.