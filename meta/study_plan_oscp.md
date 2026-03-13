# Meta: study_plan_oscp – Operational Plan for PEN-200 / OSCP+

This document is not a motivation sheet but an **operational plan** for OSCP preparation under real constraints.  
It exists to translate the broader certification roadmap into one controlled offensive phase.

OSCP is not treated here as a starting point.  
It is treated as the consolidation phase after prior foundations, reporting habits and attack logic already exist.

---

## 1. Position in the Roadmap

This file covers the OSCP phase only.  
It assumes the following progression:

- CompTIA PenTest+ completed
- THM SEC1 completed before OSCP phase
- THM SAL1 completed before OSCP phase
- THM PT1 completed before OSCP phase

This means OSCP preparation does not begin from zero.  
It begins after core methodology, triage discipline, basic reporting and junior-level offensive flow already exist.

Parallel theory track remains active during this phase:

- ISC2 CC
- CSI Linux Investigator

These parallel tracks are not the main offensive workload.  
They exist to reinforce theory, terminology, investigation logic and defensive translation during lower-energy slots.

The next phase after OSCP+ is CRTM.  
OSCP therefore functions as the bridge between structured junior offensive work and higher-order red-team operations.

---

## 2. Objective of This Phase

The purpose of this phase is not mere exam participation.  
The purpose is to build a **reproducible offensive system** that survives time pressure, fatigue and interruption.

Primary objective:

- Pass OSCP+ with stable and auditable methodology

Secondary objectives:

- Stabilise enumeration under pressure
- Reduce wasted time caused by tool-hopping and premature exploitation
- Make privilege escalation decisions more structured
- Train reporting as part of the attack chain, not as post-processing
- Produce reusable outputs for `methodology/`, `reports/` and `labs/`

Success in this phase is defined by two outputs:

- exam readiness
- repository maturity

If the exam is passed but the methodology remains chaotic, the phase is only partially successful.  
If the methodology becomes stable, the phase remains valuable even before exam day.

---

## 3. Entry Conditions

OSCP preparation begins only when the following conditions are true:

- Core note structure in `labs/`, `methodology/` and `reports/` is already usable
- CoRH is consistently applied during normal sessions
- Linux and Windows privilege escalation are no longer unfamiliar problem spaces
- Reporting no longer depends on memory reconstruction after the session
- Personal Rules and Energy Threshold are already operational, not theoretical

This matters because OSCP punishes unstable workflow more than missing trivia.  
A candidate with imperfect knowledge but disciplined methodology is more durable than a candidate with broad knowledge and no process control.

If these conditions are not met, the correct action is not to push harder.  
The correct action is to delay the OSCP phase and repair the missing operational layer first.

---

## 4. Weekly Structure

This phase runs in focus slots, not vague weekly ambition.

### Standard Weekly Structure

- **Mon–Thu**  
  One offensive slot per day, depending on energy state.  
  Focus: enumeration, exploitation or privilege escalation on one defined target or one defined problem.

- **Fri**  
  Maintenance and review slot.  
  Focus: note cleanup, CoRH correction, report refinement, screenshot sorting and methodology consolidation.

- **Sat**  
  Primary offensive day.  
  Focus: full-chain work, mock-exam segments, longer exploitation flow and structured retries.

- **Sun**  
  Recovery and meta-analysis.  
  Focus: weekly review, gap analysis, theory reinforcement and roadmap adjustment.  
  No random “one more box” behavior.

### Slot Types

- **Deep-Work Slot**  
  Used for full enumeration, exploitation or privilege escalation reasoning.

- **Maintenance Slot**  
  Used for report cleanup, evidence ordering, note repair and method correction.

- **Learning Slot**  
  Used for theory, review of weak concepts, failed-path analysis and reinforcement of recurring patterns.

### Weekly Priority Order

1. Enumeration quality
2. Privilege escalation logic
3. Reporting discipline
4. Speed only after structure is stable

The week is therefore not measured by how many machines fall.  
It is measured by whether the method becomes cleaner, faster and more reproducible.

---

## 5. Training Focus During the OSCP Phase

The OSCP phase concentrates on a narrower and harsher problem space than earlier certifications.  
Training must therefore become more selective.

### A. Enumeration as Primary Decision Engine

Enumeration is the first-class activity of this phase.  
No target moves into exploitation until service understanding has reached an acceptable threshold.

Training focus:

- service triage
- web attack-surface reduction
- authentication opportunities
- user-to-admin path recognition
- early rejection of dead branches

Rule:  
When progress stalls, return to enumeration before escalating tool complexity.

### B. Privilege Escalation as Structured Pattern Work

Privilege escalation must be trained as pattern recognition, not exploit roulette.

Training focus:

- Linux local enumeration
- Windows local enumeration
- credential discovery and reuse
- service abuse and misconfiguration
- scheduled tasks, permissions, tokens and paths
- environment-specific escalation logic

The purpose is not to remember every trick.  
The purpose is to identify which class of escalation is plausible on a given host.

### C. Reporting as Live Operational Artifact

Reporting is not deferred to the end.  
It is generated during the chain.

Training focus:

- proof collection while operating
- timeline clarity
- evidence discipline
- concise explanation of why a step mattered
- screenshots only where they preserve operational context

A chain without contemporaneous reporting is considered operationally degraded, even if access is achieved.

### D. Mock Pressure and Time Fragmentation

OSCP pressure must be simulated before exam day.

Training focus:

- fragmented multi-slot attack chains
- resume after interruption
- continue after failed exploit branch
- stop/reassess discipline
- maintain logic while tired but still above threshold

The point is not to cosplay the exam every week.  
The point is to remove surprise from pressure.

---

## 6. Integration with the Meta Layer

This plan does not stand alone.  
It operates as part of the Meta layer.

### Link to `constraints.md`

- Time defines how many meaningful slots exist
- Energy determines which task type is allowed
- Context decides whether the current mode is Normal, Exam or Recovery

If constraints are ignored, this study plan becomes fiction.

### Link to `personal_rules.md`

- No half-baked exploit chains
- CoRH mandatory
- Energy Threshold enforced
- defensive translatability preserved

If Personal Rules fail, OSCP preparation degrades into random lab activity.

### Link to Parallel Theory Track

ISC2 CC and CSI Linux Investigator continue in parallel, but only as secondary load.

Their role during the OSCP phase:

- reinforce security vocabulary
- strengthen defensive interpretation
- improve analytical discipline during lower-energy periods
- prevent an “all offense, zero theory” imbalance

They are not allowed to displace primary offensive deep-work.  
They support the phase; they do not define it.

---

## 7. Review Logic and Exit Criteria

Every week ends with explicit review.  
The phase ends only when exit conditions are visible.

### Weekly Review Questions

- Where did progress break: enumeration, exploitation, privilege escalation or reporting?
- Which failure was technical, and which failure was cognitive?
- Did Attentional Collapse indicators appear?
- Did CoRH remain intact across interruptions?
- Which recurring weakness belongs in `methodology/` rather than in a one-off note?

### Exit Criteria for Exam Readiness

The OSCP phase is considered mature when the following are true:

- enumeration no longer collapses under pressure
- failed exploit paths are abandoned without emotional attachment
- privilege escalation is approached as structured reasoning, not guesswork
- reporting can be produced from live notes without reconstruction panic
- multiple full chains exist in `reports/`
- mock sessions show recovery after interruption without major context loss

At that point, the exam becomes the validation event, not the beginning of real methodology.

---

## Key Principle

OSCP preparation is not an isolated sprint.  
It is the phase in which earlier certifications are compressed into an operationally reliable offensive method.

The exam is only one output.  
The deeper objective is to produce a system that can think, stop, resume, report and improve under pressure.

If that system exists, OSCP becomes a target.  
If it does not exist, OSCP becomes a stress amplifier.
