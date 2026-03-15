# 01_theory.md

# Theory

## Definition
IDOR stands for Insecure Direct Object Reference.

It describes an access control weakness in which a user can access or manipulate an object by modifying a direct reference to it.

## Core Problem
The application accepts a client-supplied object reference, such as:
- `user_id`
- `order_id`
- `invoice_id`
- `document_id`

The backend then processes that reference without verifying whether the referenced object belongs to the authorization scope of the current user.

## Decision Architecture of the Failure
The vulnerable logic usually looks like this:

1. The client requests object `X`.
2. Object `X` exists.
3. Therefore object `X` is returned.

The missing stage is:
4. Is the current user actually allowed to read, modify, delete, or export object `X`?

## Why URL Manipulation Is Only a Symptom
Changing a URL parameter is not the vulnerability itself.

It is only the method that makes the missing object-level authorization visible.

## Typical Patterns
IDOR commonly appears in:
- user profiles
- invoices and orders
- tickets and support cases
- export and download functions
- API endpoints with direct IDs
- object-related status changes
- reset, approval, or management flows

## Horizontal and Vertical Direction
Horizontal escalation:
a user accesses another user's object within the same privilege class.

Vertical escalation:
a user reaches objects or functions belonging to a higher privilege tier.

## Systemic Interpretation
IDOR is not primarily an input validation problem.

It is broken access control at object level.

That means:
the issue is not the format of the identifier, but the missing binding between identity, object, and permitted action.
