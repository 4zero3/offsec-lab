# Decision Points

## Scope

This file defines how defensive work should identify,
interpret, and harden decision points inside normal operational workflows.

The focus is not on isolated malicious artifacts,
but on the moment where a person shifts from
**verification** to **execution**
under pressure, context, authority, routine, or ambiguity.

It translates human-factor risk into defensive logic.

This file is not a phishing checklist.  
It is a structural model for where secure behavior
must be protected inside real work.

---

## Objective

The objective is to identify where exploitability emerges
inside otherwise legitimate business activity.

A decision point becomes relevant when:

- a concrete action is requested
- verification would still be possible in theory
- context makes verification less likely in practice
- pressure, familiarity, or responsibility compress reflection
- execution begins to feel more important than checking

The defensive goal is not permanent suspicion.  
It is to make unsafe execution harder than safe verification.

---

## Core Principle

> Defense should not only detect malicious content.  
> It should interrupt the decision that would make the content effective.

This means defensive design must ask:

- where does action begin
- where does checking weaken
- which process layer should absorb or slow the decision
- how can secure friction be introduced without breaking operations

The decisive question is not only
whether a message looks suspicious,
but whether the target is still operating
in a state where verification remains behaviorally realistic.

---

## What a Decision Point Is

A decision point is the moment at which a target
must choose between execution and verification.

From a defensive perspective,
a decision point matters when four elements converge:

1. **Action demand**  
   A specific step is requested:
   click, approve, transfer, confirm, disclose, log in, bypass, escalate.

2. **Reduced verification capacity**  
   Checking is still possible,
   but no longer likely under the present conditions.

3. **Plausible operational framing**  
   The request appears to belong to ordinary work,
   not to an obviously anomalous event.

4. **Compressed judgment**  
   Urgency, context, hierarchy, responsibility,
   relief, or routine push the target toward execution.

If these conditions align,
the system must not rely on vigilance alone.

---

## Why Decision Points Matter

Security failure in human workflows rarely begins
with total loss of judgment.

It usually begins with a smaller shift:

- the request seems to fit
- the timing seems plausible
- the action seems urgent
- the context seems familiar
- the secure pause feels costly

That is the defensive importance of decision points.  
They are the places where verification does not disappear instantly,
but becomes progressively less probable.

If those moments are not protected,
the workflow itself becomes part of the vulnerability.

---

## Decision Point Model

Decision points can be understood
as moments of shrinking verification capacity.

The pattern is usually not:

1. suspicious input appears  
2. user fails to notice it  
3. compromise occurs  

The pattern is more often:

1. a request enters a familiar context  
2. legitimacy is inferred from fit  
3. pressure narrows interpretation  
4. execution begins to dominate  
5. verification becomes behaviorally unlikely  

This is why artifact-centered defense is incomplete.  
It misses the operational moment
where secure behavior becomes harder than insecure behavior.

---

## Typical Defensive Decision Points

### 1. New Action inside Familiar Context

A workflow introduces a new step,
but frames it as a continuation of something known.

Examples:

- “use the updated endpoint”
- “approve it directly this time”
- “the internal route is delayed”
- “please confirm manually for now”

**Defensive relevance:**  
The target does not primarily verify authenticity.  
The target verifies whether the request seems to belong.

**Risk:**  
Context substitutes for legitimacy.

**Defensive need:**  
Validate action changes, not sender familiarity alone.

---

### 2. Authority-Coupled Execution

The requested action is tied to hierarchy,
escalation pressure, or perceived strategic importance.

Examples:

- direct request from senior leadership
- subtle blame for delay
- references to known internal priorities
- phrasing that frames inaction as obstruction

**Defensive relevance:**  
Authority compresses doubt
when verification is socially weaker than compliance.

**Risk:**  
Process logic is replaced by role logic.

**Defensive need:**  
Authority must never remove verification requirements.

---

### 3. Time-Compressed Approval

A narrow time window is attached to the action.

Examples:

- “before noon”
- “this must go out today”
- “I need this cleared now”
- “confirm in the next 10 minutes”

**Defensive relevance:**  
The target increasingly optimizes for completion speed.

**Risk:**  
Reflection is recoded as delay.

**Defensive need:**  
Sensitive actions require pause rules
that remain legitimate under urgency.

---

### 4. Relief-as-Solution Moment

A workaround appears exactly when
the normal process feels blocked, slow, or frustrating.

Examples:

- “the internal route is still not moving”
- “use the fallback link”
- “we’ll fix the system later”
- “this is the quickest path for now”

**Defensive relevance:**  
The request does not only demand action.  
It offers relief.

**Risk:**  
Relief suppresses checking more effectively
than overt aggression.

**Defensive need:**  
Fallbacks must be predefined, documented,
and independently verifiable.

---

### 5. Multi-Channel Reinforcement

The same request is repeated or reinforced
through another channel such as phone or chat.

Examples:

- email + call
- email + follow-up ping
- “did you see the mail?”
- “just confirming that this is the one”

**Defensive relevance:**  
The second channel is often misread as confirmation.

**Risk:**  
Social continuity is mistaken for proof.

**Defensive need:**  
Staff must understand:
channel multiplication is not verification.

---

### 6. Post-Commitment Acceleration

The target has already taken a small step,
and pressure is increased for fast completion.

Examples:

- “all good?”
- “I need to report this now”
- “just finalize it”
- “let me know once done”

**Defensive relevance:**  
Once partial commitment exists,
reversal becomes cognitively and socially more expensive.

**Risk:**  
The target continues not because trust increased,
but because disengagement became harder.

**Defensive need:**  
Controls must exist before and during commitment,
not only after completion.

---

## Verification Failure Modes

Decision points usually degrade through one or more
predictable failure modes.

### Context Substitution

The target checks fit, not authenticity.

The event seems to belong,
so independent verification weakens.

### Authority Override

Role hierarchy suppresses procedural hesitation.

The target acts because the source appears entitled to bypass friction.

### Urgency Compression

Time pressure narrows cognitive bandwidth.

The target no longer asks what is true,
but what must be finished.

### Routine Absorption

Repeated workflow patterns reduce attention.

The target classifies the event as normal process noise.

### Relief Capture

A workaround appears as resolution.

The target is grateful for progress
and becomes less likely to inspect the route.

### Commitment Lock-In

Partial engagement increases continuation pressure.

The target feels already involved,
so doubt becomes more costly.

These are not moral failures.  
They are predictable outputs
of weakly defended decision environments.

---

## Defensive Control Logic

Every relevant decision point should map
to one or more control layers.

### Technical Controls

Technical controls are strongest
where actions pass through infrastructure.

Examples:

- link isolation and sandboxing
- domain mismatch detection
- step-up authentication
- conditional access
- anomaly scoring
- session correlation
- behavior analytics
- SIEM patterning

Technical controls help where the workflow
still leaves observable signals.

They are necessary,
but not sufficient on their own.

---

### Process Controls

Process controls matter where
the artifact may appear plausible,
but the workflow deviation is the true signal.

Examples:

- no approvals via external links
- no spontaneous fallback paths
- documented exception handling only
- second-person verification for sensitive approvals
- known callback channels only
- role-based actions must remain process-bound
- informal email instruction cannot redefine approval logic

A strong process absorbs pressure
instead of transmitting it directly to the individual.

---

### Human Controls

Human controls are not about blame.
They are about preserving usable verification behavior.

Examples:

- notice when checking has stopped
- treat urgency + authority + new action as stop combination
- normalize delay for verification
- treat workaround language as a risk signal
- treat second-channel reinforcement as potential pressure, not proof
- make escalation socially legitimate

Human controls must be rehearsable
and behaviorally realistic under stress.

---

## Decision Stop Logic

A **decision stop** is a deliberate interruption
inserted at the point where execution begins
to replace verification.

A good decision stop is:

- simple
- fast
- policy-backed
- socially legitimate
- stronger than the immediate pressure of the event

A decision stop should trigger when:

- a new route or endpoint appears
- a sensitive action is requested through unfamiliar means
- authority and urgency converge
- a known process is bypassed “just this once”
- a second channel appears to confirm the same action
- workaround language appears during active pressure

The purpose of the stop is not delay for its own sake.  
It is to restore metacognitive distance
before execution becomes automatic.

---

## Decision Stop Questions

Useful defensive decision stops do not begin with
“Does this look malicious?”

They begin with questions like:

- Am I still checking, or am I already just finishing?
- Is this request verified, or merely familiar?
- Is urgency replacing process?
- Has the route changed, even if the story feels normal?
- Does this second channel actually verify anything?
- Would I still do this if the same request came without pressure?

These questions are valuable
because they target decision conditions,
not only message appearance.

---

## Kaizen Loop

Decision points should not remain theoretical.  
They must be tested, measured, and hardened iteratively.

### Loop

1. Simulate or observe a realistic workflow under pressure  
2. Identify where verification weakened or disappeared  
3. Log the exact decision point where execution took over  
4. Classify the weakness:
   - technical
   - process
   - human
   - state / timing  
5. Introduce one targeted control or redesign  
6. Re-run and compare  
7. Retain only what improves real resilience  

### Key Question

Not: “Did the user click?”  
But: **At which decision point did the stop fail?**

This produces more useful defensive learning
than artifact-focused awareness metrics.

---

## Relationship to the Quarter-End Scenario

The quarter-end scenario is one concrete case
through which these decision points can be observed.

### Upstream Scenario

- `psychology/07_applied_se_scenario_quarter_end.md`  
  Defines the scenario, Verification Bands,
  and the progressive reduction of verification capacity.

### Consolidated Case Reading

- `psychology/08_quarter_end_case_study.md`  
  Preserves the case-based defensive interpretation
  and its structural lessons.

This file is the abstraction layer between both:
it extracts reusable defensive logic
from a specific scenario.

---

## Defensive Use

This file is intended for:

- workflow hardening
- process design
- blue / purple team exercises
- state-aware awareness design
- human-centered threat modeling
- post-incident control analysis

It should be used to improve how organizations
protect the moment of decision,
not merely how they classify suspicious artifacts.

---

## Final Note

If a workflow makes insecure execution easier
than safe verification,
the workflow is part of the vulnerability.

Decision points matter because they reveal
where security actually succeeds or fails:
not only at the level of content,
but at the level of conditions under which people act.

The defensive task is therefore not to expect perfect users.  
It is to build processes in which secure interruption
remains normal, fast, and legitimate.