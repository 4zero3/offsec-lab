# 04_defense-prevention.md

# Defense - Prevention

## Principle
IDOR is not prevented by making identifiers difficult to guess.

It is prevented by enforcing authorization for every object-related action on the server side.

## Architectural Rule
The application must never decide what to return or modify solely on the basis of a client-supplied object identifier.

Instead, the target object must always be resolved within the authorization context of the current user.

## Secure Direction
Unsafe:
- load order by `id = request.order_id`

Safer:
- load order by `id = request.order_id`
- and `owner = current_user`
- or within the permitted tenant, team, or role scope

## Technical Controls
- enforce ownership checks in the data access path
- enforce scope checks for roles, tenants, teams, or business units
- centralize object authorization in policies, guards, or authorization services
- never trust client-supplied `user_id` values as proof of entitlement
- authorize export, download, and special actions separately

## Important Design Point
Complex or unguessable identifiers may reduce trivial enumeration.

They do not replace authorization.

## Query Pattern
Unsafe:
`SELECT * FROM orders WHERE id = :id`

Safer:
`SELECT * FROM orders WHERE id = :id AND user_id = :current_user`

## API Rule
Every endpoint that touches an object should explicitly answer:
- who is calling?
- which object is targeted?
- which action is requested?
- within which scope is that action valid?
