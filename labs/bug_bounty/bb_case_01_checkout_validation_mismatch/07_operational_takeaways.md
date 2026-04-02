# Operational Takeaways – Address Consistency Failure

## Key Takeaways
- form-level validation is not an authoritative control
- workflow continuity matters more than isolated validation signals
- preview is not proof by itself
- persistence is the decisive boundary
- contradictory state must be tracked across the full workflow

## Reusable Method
- introduce contradiction
- observe whether the workflow accepts it
- check whether preview carries it forward
- verify whether persistence preserves it

## Case Value
The value of the case is not the initial validation error.

The value of the case is that contradictory state survived workflow transitions and appeared in stored order data.