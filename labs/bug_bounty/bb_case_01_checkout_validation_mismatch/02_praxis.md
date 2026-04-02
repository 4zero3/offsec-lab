# Praxis – Address Consistency Execution (Real Scenario_bug_bounty)

## Step 1 – UI Baseline
Contradictory country/address combination introduced.

Observed:
- frontend validation error triggered
- mismatch indication shown

## Step 2 – Workflow Continuation
Workflow continued without correction.

Observed:
- state remained usable
- no immediate blocking

## Step 3 – Preview Behavior
Checkout preview reached.

Observed:
- contradictory invoice / delivery representation visible
- no normalization applied

## Step 4 – Completion Path
Workflow continued through completion.

Observed:
- no blocking condition triggered
- flow reached final state

## Step 5 – Persistence Check
Order state reviewed after completion.

Observed:
- contradictory data in stored order view
- contradiction persisted