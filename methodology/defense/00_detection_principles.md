# Defense: Detection Principles

This chapter defines detection not as a single rule, but as the structural ability to make security-relevant activity visible under real conditions.

Detection does not begin with an alert.
Detection begins with the question of which parts of a system are observable at all, with what quality that observation exists, and under which conditions activity becomes actionable signal.

This chapter therefore comes before `01_log_sources.md`, `02_alert_patterns.md` and `03_triage_and_escalation_logic.md`.
It does not describe concrete tools, but the reasoning model on which later detection depends.

---

## 1. Detection is visibility under constraint

Detection is the ability to derive reliable indicators of security-relevant activity from incomplete telemetry.
It never works with complete truth, only with observable traces.

For that reason, detection is not a binary system of “seen” or “not seen”.
It is always bounded by coverage, quality, context and time.

The first question is not:
“Which rule fired?”

It is:
“Which activity is visible in this system at all?”

---

## 2. Signal matters more than volume

More data does not automatically mean better detection.
Unfiltered telemetry creates noise, analyst load and prioritisation failure.

Good detection does not maximise log volume.
It maximises signal quality.

It prefers observations that are:
- security-relevant
- context-ready
- reproducibly interpretable
- usable during triage

Signal without context produces false positives.
Context without signal produces blindness.
Detection needs both.

---

## 3. Telemetry exists before every rule

There is no detection without visibility.
Where usable telemetry does not exist, reliable detection cannot exist either.

Logs, endpoint data, network metadata, identity traces and cloud events are not finished detections.
They are raw material.

Telemetry is therefore not a side topic.
It is the material foundation of detection.

Weak telemetry produces weak rules.
Missing telemetry produces false confidence.

---

## 4. Detection is correlation, not isolated event

An isolated event is rarely meaningful on its own.
Usable detection often appears only when several weak signals are linked.

A single failed login may be normal.
Repeated failures followed by a successful login, process activity and data access create operational meaning.

Detection therefore asks not only:
“What happened?”

But:
“Which events together form a durable hypothesis?”

---

## 5. Detection is iterative, not static

Detection rules are not final truths.
They must be tested, evaluated, refined and compared against real behaviour.

Every detection creates follow-up questions:
- Was the signal useful?
- Was it too broad?
- Was it too late?
- Was context missing?
- Was the detection technically correct but operationally weak?

Detection is therefore not a finished product.
It is a continuous process of tuning and learning.

---

## 6. Good detection serves decision

The purpose of detection is not alert production.
The purpose is to enable better and faster decisions.

A good detection must therefore be:
- triage-ready
- prioritised
- escalatable
- understandable to other analysts

If a detection fires but prepares no usable decision, it remains operationally limited.

---

## 7. Detection failure is not exception, but information

Every missed detection reveals something about the limits of the system.
Failures are not only defects, but indicators of blind spots in telemetry, logic, timing or assumptions.

For that reason, detection failure is not only an end chapter.
It is already embedded in the principles:
Every detection should be designed under the question of how it will fail.

---

## Boundary of this chapter

This chapter does not cover:
- Sigma rules
- SPL/KQL syntax
- SIEM-specific workflows
- product-specific queries

Those follow only indirectly from the principles.
`00_detection_principles.md` defines the reasoning base, not the tooling.

---

## Key Principle

Detection is the controlled reduction of uncertainty from incomplete visibility.
Not every activity becomes visible.
Not every visible activity is signal.
Not every signal is decision-ready.

The task of defensive methodology is to structure those transitions deliberately.
