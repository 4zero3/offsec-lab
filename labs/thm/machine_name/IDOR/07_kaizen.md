# 07_kaizen.md

# Kaizen

## Purpose
This section does not repeat the finding.

It exists to improve analytical quality, repeatability, and future decision-making.

## Delta From This Lab
- mark direct object references earlier as likely control boundaries
- focus less on spontaneous URL manipulation and more on object model and scope
- separate object existence from authorization proof more clearly

## What Worked Well
- the reference was visible
- the object behavior was easy to observe
- the finding was reproducible with minimal ambiguity

## What Must Become More Precise
- classify object types earlier
- separate actions by object class: read, update, delete, export
- model horizontal and vertical misuse paths at the beginning, not at the end

## Reusable Question
If an application exposes a direct object reference:
who may use which object, with which action, and under which server-side rule?

## Maturity Rule for the Next Iteration
For the next similar web lab, follow this order:

1. identify the object class
2. identify the scope
3. identify the action
4. state the authorization assumption
5. validate that assumption deliberately
6. write the defensive implication immediately

## Transition to Reports
Once theory, practice, result, and defense are stable, this node can be condensed into a report.

The lab remains the raw operational space.
The report becomes the reproducible end form.
