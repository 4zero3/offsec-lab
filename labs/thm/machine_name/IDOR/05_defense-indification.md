# 05_defense-identification.md

# Defense - Identification

## Goal
IDOR must be treated as a systematic testing class.

Its detection should not depend on luck or only on visible numeric identifiers.

## Review Strategy
For each application and API, all object access paths should be inventoried first.

This includes:
- path parameters
- query parameters
- body fields
- hidden form fields
- download links
- export endpoints
- state-changing operations
- administrative object functions

## Core Review Questions
For every object-related endpoint, ask:

1. Can one user address another object of the same class?
2. Are read, update, delete, and export authorized independently?
3. Does the application return `200` where `403` or `404` should be expected?
4. Do errors or metadata leak the existence of foreign objects?
5. Is authorization centralized or scattered across controller logic?

## Testing Directions
- test horizontal access control
- test vertical access control
- test tenant boundaries
- test download and export paths
- test API and UI paths separately

## Logging and Monitoring
Security-relevant indicators include:
- repeated requests to adjacent object references
- access attempts against foreign resources
- clustered `403` or `404` responses in narrow object ranges
- anomalies in export and download behavior

## Developer-Facing Detection
IDOR should already stand out during code review when an object is loaded directly from client input without ownership or scope enforcement in the same control path.

A strong review indicator is any place where an object is fetched by primary key and then returned or modified without a clear authorization gate.
