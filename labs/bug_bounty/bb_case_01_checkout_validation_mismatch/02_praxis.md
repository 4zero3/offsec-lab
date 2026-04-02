# Praxis – Address Consistency Execution (Real Scenario_bug_bounty)

## Initial Situation

**Target Type:** authenticated e-commerce checkout workflow  
**Target:** private bug bounty target redacted

The case did not begin with a confirmed finding.

It began with one operational question:

> Does contradictory address state remain local to the form, or does it survive workflow transitions?

---

## Execution Logic

The investigation followed a controlled path:

- introduce contradictory address state
- observe frontend behavior
- continue the workflow
- check whether the state is rejected, propagated, or persisted

The focus was not on isolated responses.

The focus was on state continuity across workflow steps.

---

## Step 1 – UI Baseline

A contradictory country/address combination was introduced.

Observed behavior:

- frontend validation error triggered
- mismatch between country and address components indicated

Interpretation:

> the system detects inconsistency at UI level

At this point, the case remained ambiguous.

---

## Step 2 – Accepted Workflow State

The contradictory state was not treated as a local form artifact only.

Observed behavior:

- the state remained usable within the workflow
- no decisive consistency boundary stopped progression at this stage

Interpretation:

> visible validation does not define final acceptance

---

## Step 3 – Preview Behavior

The checkout preview was reached with the contradictory state still present.

Observed behavior:

- contradictory invoice / delivery representation visible
- no normalization applied before preview

Interpretation:

> the workflow carries forward contradictory state

---

## Step 4 – Completion Path

The workflow continued through checkout completion.

Observed behavior:

- no blocking condition triggered
- the flow reached its final state

Interpretation:

> no decisive consistency enforcement exists before completion

---

## Step 5 – Persistence Check

The resulting order state was reviewed after completion.

Observed behavior:

- contradictory address data appeared in the stored order view
- the contradiction persisted beyond workflow execution

Interpretation:

> the system accepts contradiction as persisted state

---

## Execution Path Summary

inconsistent input  
→ UI detects issue  
→ accepted workflow state remains usable  
→ preview reflects contradiction  
→ completion succeeds  
→ persisted state remains inconsistent

---

## Core Observation

The decisive factor was not detection.

The decisive factor was:

> the system did not enforce consistency at any persistence-relevant boundary

---

## Key Learning

> A validation signal has no value if it is not enforced across workflow transitions.