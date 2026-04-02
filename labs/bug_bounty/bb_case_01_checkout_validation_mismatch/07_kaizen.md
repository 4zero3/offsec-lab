# Kaizen – Address Consistency Failure

## Core Lesson

The case was not solved by exploring more.

It was solved by following one contradiction through the full workflow.

---

## Effective Method

- detect contradiction
- test backend acceptance
- observe workflow continuation
- verify persistence

> Only the full chain produces a valid result.

---

## Key Correction

Do not treat validation as a UI problem.

Treat validation as a persistence problem.

---

## Pattern

- validation exists
- validation is not authoritative
- layers disagree
- contradiction survives

---

## Reusable Approach

find contradiction → test acceptance → test propagation → test persistence

---

## Insight

The strongest findings are broken invariants, not isolated anomalies.

---

## Learning

Validation only matters if enforced at persistence boundaries.