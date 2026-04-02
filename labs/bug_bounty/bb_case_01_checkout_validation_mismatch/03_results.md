# Results – Address Consistency Failure (Real Scenario_bug_bounty)

## Final Result
> The system did not enforce one authoritative address consistency state across the observed workflow.

Contradictory address data was:
- introduced
- accepted by backend-supported workflow
- visible in checkout preview
- carried through order completion
- persisted in final order records

## Core Finding
> inconsistent address state survived from workflow handling into final stored order data

## Result Chain
1. **UI Validation Exists**: country/city mismatch detected
2. **Validation Not Enforced**: backend mutation accepted inconsistent data  
3. **Preview Does Not Reconcile**: contradictory state displayed
4. **Workflow Continues**: no blocking before completion
5. **Persistence Confirms**: inconsistency stored in order records

## What Was Proven
- backend accepts inconsistent data
- checkout propagates inconsistency
- order persistence preserves contradiction

## What Was Not Proven
- cross-user impact
- privilege escalation
- payment manipulation

Strictly single-user workflow integrity failure.