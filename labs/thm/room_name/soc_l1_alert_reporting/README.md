# THM: SOC L1 Alert Reporting

## Scope

This entry documents the operational takeaways from the TryHackMe room **SOC L1 Alert Reporting**.  
It is not a walkthrough and not a task-by-task reproduction.  
Its purpose is to translate the reusable logic behind alert reporting, escalation and communication into a durable form.

---

## Objective

The focus of this entry is not tool usage, but the quality of the L1-to-L2 handoff.  
The main question is how an analyst turns alert data into a report that remains operationally useful to downstream analysis.

Core goals:

- understand reporting as an operational artifact
- preserve investigative context for L2
- state escalation reasons clearly
- handle communication edge cases in a structured way
- derive reusable repository structure from room content

---

## Core Concepts

The room makes clear that reporting is not an administrative ending step.  
It is part of incident handling itself.

A good alert report should:

- include the 5Ws
- form one coherent timeline
- attach relevant evidence and indicators
- make the escalation reason explicit
- reduce unnecessary reconstruction work for L2

This shifts reporting from post-analysis documentation to documentation as part of analysis.

---

## Operational Takeaways

### 1. Reporting preserves context

A well-written report saves L2 time and reduces ambiguity.  
It acts as the first durable context container of the case.

This matters because raw SIEM data does not always remain equally accessible, searchable or coherent over time.  
The report therefore preserves case context beyond the immediate triage window.

### 2. The 5Ws are the minimum structure

The 5Ws form the minimum structure of a usable alert report:

- **Who** – which user or process was involved
- **What** – which activity or event sequence was observed
- **When** – when the activity began or occurred
- **Where** – which system, IP or resource was involved
- **Why** – why the final verdict was reached

This structure is simple, but operationally strong.  
It prevents fragmented notes and forces a traceable timeline.

### 3. Escalation requires justification

An alert is not simply forwarded.  
Escalation is only useful when it clearly explains why L2 involvement is necessary.

Typical escalation reasons include:

- deeper investigation is required
- malware behaviour exceeds L1 scope
- further containment decisions are needed
- confirmed malicious activity is present
- evidence suggests broader impact or follow-on actions

### 4. Communication is part of defense

Communication failures are not side notes.  
They are part of real SOC operations.

Important edge cases include:

- critical alert but L2 is unavailable
- compromised communication channel requiring out-of-band validation
- alert flood with multiple critical cases at once
- delayed recognition of a previous misclassification
- SIEM logs are incomplete or not usable

These cases show that defensive quality depends not only on analysis, but also on coordination.

---

## Example Case Logic

A strong example in the room is a **Double-Extension File Creation** case involving a suspicious download followed by escalation.  
The value of that case lies not in report length, but in report clarity.

The case shows that a good report combines:

- a clean timeline
- user and host context
- malware relevance
- escalation reasoning
- a clear handoff to L2

A useful report is therefore not maximally long.  
It is precise, evidence-based and operationally actionable.

---

## Reporting Checklist

The checklist shown in the room defines a practical minimum standard for alert reporting:

- all 5Ws are included
- the report is clear and precise
- the report forms a single coherent timeline
- evidence and indicators are attached
- the escalation reason is explained

These points are a strong reusable baseline for future defensive case handling.

---

## Communication and Escalation Cases

The room presents several communication and escalation scenarios that matter in practice:

- critical alert but L2 is unavailable
- account or chat compromise requires alternate contact validation
- high alert volume requires prioritisation and L2 notification
- later realisation that a case was misclassified
- triage cannot be completed because SIEM data is incomplete or not searchable

These scenarios make clear that SOC work is not only technical analysis, but also workflow stability.

---

## Repository Mapping

This hands-on entry maps primarily to the following repository areas:

- `methodology/defense/03_soc_triage_logic.md`
- `methodology/defense/04_detection_failures.md`

Its operational value lies not in completing the room itself, but in converting it into reusable structure.

---

## Screenshots

Supporting screenshots for this entry are stored in:

`./screenshots/`

They document in particular:

- escalation and communication cases
- the 5W structure
- the reporting checklist
- an example alert report layout

---

## Reflection

The main lesson is that good L1 work is not defined only by correct classification.  
It is defined by whether the next analyst can continue the case without rebuilding the context from scratch.

Alert reporting therefore functions as an operational bridge between triage and deeper investigation.  
For that reason, it is not administrative overhead, but a core defensive capability.
