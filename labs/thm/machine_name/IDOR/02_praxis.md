# 02_practice.md

# Practice

## Starting Point
The application exposed a resource through a direct object reference.

A valid order or invoice reference was visible to an authenticated user and could be addressed directly through the request path.

## Observation
A legitimate reference was modified in the browser.

The value `1234` was changed to `1000`.

## Result of the Change
After sending the modified request, the application did not return:
- an authorization failure,
- a generic error,
- or an empty response.

Instead, it returned invoice or order data associated with another user.

## What Was Proven
This did not merely show that object `1000` exists.

It showed that the backend resolves and returns the requested object based on its identifier without validating whether the current user is authorized to access that object.

## Operational Conclusion
The server-side logic appears to follow a pattern similar to:

- read object ID from the request
- query the object by that ID
- return the object if found

The missing control question is:
- does this object belong to the current user or to the user's allowed scope?

## Strategic Testing Path
The ID change was only the validation step for a previously visible access pattern.

A cleaner strategic approach is:

1. identify all direct object references first,
2. determine the current user's authorization scope,
3. separate actions by object type,
4. then validate whether read, update, delete, and export are enforced independently.

## Important Analytical Point
Not every editable identifier is automatically a security issue.

It becomes a security issue when the referenced object lies outside the user's allowed ownership or role scope and the server still processes it.

## Technical Reading of the Case
The browser did not bypass security on its own.

It simply sent a new HTTP request for a different object.

The vulnerability existed entirely in the server-side authorization logic.
