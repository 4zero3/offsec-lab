# Address Consistency Failure

## Context

This entry documents a real black-box investigation against a private e-commerce checkout and order workflow.

The focus was narrow and deliberate.

The case did not attempt broad exploitation.
It focused on one concrete question:

> Does the system enforce one logically consistent address state across editing, preview, order completion, and stored order data?

The observed answer was no.

---

## Core Finding

The tested platform did not enforce address consistency uniformly across the observed workflow.

A contradictory address state could be:

- introduced through normal interaction
- remain usable within the workflow
- displayed in checkout preview
- carried through order completion
- persisted in final order data

This makes the issue stronger than a frontend validation artifact.

The relevant path is:

**introduced → accepted → propagated → persisted**

---

## Why This Matters

The case is not interesting because a form showed an error.

The case is interesting because the system still treated contradictory state as valid enough to preserve.

That turns the issue into a business-logic integrity problem.

The important question was never:

> “Did the frontend complain?”

The important question was:

> “Did the system still keep the contradiction?”

It did.

---

## Practical Structure

This entry is split into the following parts:

### `01_scope.md`
Defines the exact target surface, question, and constraints.

### `02_praxis.md`
Documents the real execution path and the transitions that mattered.

### `03_results.md`
States the validated result chain and the final conclusion.

### `04_dead-ends.md`
Documents interpretations and paths that were investigated and rejected.

### `05_defense-identification.md`
Identifies the control failure conceptually.

### `06_defense-improvement.md`
Describes how the issue should be prevented.

### `07_kaizen.md`
Captures the operator lesson from the case.

---

## Central Pivot

The decisive transition in this case was the moment contradictory state stopped being a local form anomaly and became accepted workflow state.

From there, the case became materially stronger because preview, completion, and persistence could be evaluated against a state the system had already accepted.

---

## Evidence Logic

This entry does not rely on one screenshot or one isolated artifact.

It relies on a sequence.

### UI signal
- inconsistent country/address combinations trigger validation feedback

### Workflow propagation
- preview displays contradictory invoice / delivery state
- checkout continues through finish

### Persistence
- order overview / order detail preserve the inconsistency

That full chain is what makes the entry report-worthy.

---

## Final Note

This case documents a black-box path where disciplined narrowing mattered more than volume.

The key lesson is simple:

> The finding was not that the UI looked strange.
> The finding was that contradictory state survived workflow transitions and became stored business data.