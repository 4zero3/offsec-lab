# Scope – Address Consistency Failure (Real Scenario_bug_bounty)

## Initial Situation
**Target Type:** authenticated e-commerce checkout workflow  
**Target:** private bug bounty target redacted

**Objective:**
> Determine whether one logically consistent address state is enforced across checkout-relevant workflow stages.

## Investigation Focus
- delivery address handling
- invoice address handling
- country / city / postcode / street consistency
- checkout preview state
- order persistence after successful flow completion

## Constraints
Single authenticated user context only.

**Not tested:**
- account takeover
- cross-user access
- payment fraud or price manipulation
- privilege escalation
- destructive automation

## Success Condition
- contradictory address state introduced
- workflow continuity without restored consistency
- reflected in final stored order data