# 06_defense-improvement.md

# Defense - Improvement

## Target State
The goal is not to patch a single endpoint.

The goal is to harden the entire object-access layer as a reusable security pattern.

## Improvement Directions

### 1. Centralization
Object authorization should live in:
- policies
- authorization services
- guards
- repository or service layers

It should not exist as scattered one-off checks in individual controllers.

### 2. Standardization
All object-related actions should follow the same sequence:
- load object
- validate scope
- validate action
- only then allow response or mutation

### 3. Regression Protection
Every fixed IDOR issue should become a test case:
- positive test for authorized access
- negative test for a foreign object
- role test for lower and higher privileges
- separate tests for export, download, and state changes

### 4. Response Behavior
The application should avoid leaking unnecessary object information.

Where operationally suitable, a neutral not-found response is often preferable to exposing foreign object existence in detail.

### 5. Architectural Maturity
Ownership, tenant scope, and role model must be visible parts of the domain model.

If these relationships are not modeled clearly, IDOR conditions tend to emerge across multiple endpoints.

## Desired End State
A corrected endpoint is not only “no longer exploitable”.

It becomes explicitly authorized, testable, and consistently hardened in a way that can be applied to similar object classes.
