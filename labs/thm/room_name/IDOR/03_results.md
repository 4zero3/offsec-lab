# 03_result.md

# Result

## Finding
An IDOR condition was confirmed.

The application allows access to a foreign object by manipulating a direct object reference within the request.

## Nature of the Weakness
This is a broken access control issue at object level.

More precisely, the application does not enforce a server-side check that binds the requested object to the current user's ownership or authorized scope.

## Evidence
The finding was validated by changing a legitimate object reference into a foreign reference.

The application responded with another user's order or invoice data instead of denying access.

## Risk
A weakness of this type may lead to:
- exposure of personal or business data
- unauthorized access to other users' records
- object modification or deletion
- privilege abuse
- follow-on attacks through information disclosure

## Operational Significance
The case demonstrates that authentication alone is not sufficient protection.

An authenticated user remains dangerous if authorization is not enforced at object level.

## Defensive Translation
Every object-related action must answer at least three questions:
- who is requesting access?
- which object is being addressed?
- which action is allowed on that object?

## Repository Relevance
The value of this lab is not the changed number.

The value lies in the reasoning chain:
a visible reference was recognized as an object boundary, tested against scope assumptions, and confirmed as a missing ownership check.
