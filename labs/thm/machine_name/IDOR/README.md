# IDOR

## Context
This directory documents a TryHackMe case on IDOR as an object-level access control failure in a web application.

The focus is not URL manipulation as a trick, but the underlying control failure:
a client-supplied object reference is processed server-side without enforcing authorization for that specific object.

## Objective
The goal of this node is to understand IDOR not as an isolated bug, but as the result of missing binding between identity, resource, and action.

This directory captures:
- the theoretical model,
- the practical validation path,
- the resulting finding,
- and the defensive translation into prevention, identification, and improvement.

## Offensive
- `01_theory.md`
- `02_practice.md`
- `03_result.md`

## Defense
- `04_defense-prevention.md`
- `05_defense-identification.md`
- `06_defense-improvement.md`

## Kaizen
- `07_kaizen.md`

## Guiding Principle
IDOR is not a number game.
Changing an object reference is only the visible surface.

The actual failure is that the backend accepts an object reference from the client without enforcing the relationship between the current identity, the requested object, and the allowed action.

## Operational Placement
This node belongs in `labs/` because it documents observations, assumptions, validation logic, and repeatability.


## ⚠ Work in progress
A later refined and exam-ready derivative can be transferred into `reports/`.
