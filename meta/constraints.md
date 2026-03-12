# Meta: Constraints – Operating Inside Hard Edges

This chapter defines the conditions under which offensive work in this repository can realistically exist.  
Constraints are not weakness but the **operational frame**: they draw hard edges that make precision possible.

The goal is not to do more, but to do the right work under known limitations.


## 1. Constraint Axes

For this repository, three primary constraint axes are in play:

- Time – available focus slots, deadlines, recovery windows  
- Energy – cognitive capacity, decision quality, fatigue  
- Context – job obligations, exams, infrastructure, private commitments  

All planning in `meta/` and all methods in `methodology/` must operate explicitly inside these axes.  
Anything that does not fit is not a stretch goal; it is out of system.


## 2. Time Constraint: Focus Slots, Not Endless Grind

Time is not measured as “hours per week” but as qualitatively defined focus slots:

- Exam-oriented deep-work blocks (90–120 minutes, zero interruptions)  
- Maintenance slots (30–60 minutes, review and light corrections)  
- Learning slots (60–90 minutes, theory, papers, tooling refinement)

Rule:  
No critical attack step or reporting step is started outside a focus slot.  
Half-baked exploit chains launched in leftover minutes are forbidden – they produce inconsistent reasoning paths.


## 3. Energy Constraint: Cognitive Quality as Hard Limit

Not every time window has the same value.  
This repository works with an explicit energy budget:

- High-energy phases → architecture, privilege escalation logic, reporting structure  
- Medium energy → tooling refinement, log analysis, error review  
- Low energy → cleaning up `labs/`, adding tags, minor markdown fixes  

**Operationalised Threshold:** Energy is below minimum when **Attentional Collapse** occurs:  
- **Reasoning loop** = returning to the same hypothesis without introducing new evidence or tools  
- Focus <10 minutes sustained  
- Context switches every 5 minutes or more  
- Repeated misoperation of known tools  

Then:
- immediate downgrade to defensive tasks
- session closure with Chain-of-Reasoning-Historie (CoRH)  
**Hypothesis → Observation → Decision → Next step**

## Energy constraints protect reasoning quality. When reasoning collapses, the system forces documentation and recovery instead of continuing degraded offensive work.


## 4. Context Constraint: Job, Exams, Infrastructure

Offensive work does not happen in isolation. Relevant contextual limits include:

- A primary job with its own priority and confidentiality  
- Exam windows (e.g. certifications) with fixed time corridors  
- Infrastructure limits (hardware, lab licenses, allowed windows for noisy tests)  
- Private commitments enforcing hard cut-off times

**Active Management Modes:**
- Mode A: Normal (full offensive)  
- Mode B: Exam (review + reporting only)  
- Mode C: Recovery (repo maintenance only)  

Attack paths that require monolithic 10-hour sessions are not modeled here.  
Instead, chains are preferred that split into clean segments which can be stopped and resumed without loss of state.


## 5. Session Recovery and Closure

Every session ends with standardised state capture:
- Current hypothesis as markdown snippet  
- Next planned step (1 sentence)  
- Open questions / dead ends  
- Logs must be reproducible from repository state.
- CoRH snapshot: Hypothesis → Observation → Decision → Next step

This enables clean resume even after 48h pause.  
No “to be continued” – only reproducible snapshots.


## 6. How Constraints Are Applied Here

Constraints are only useful if they are visible and auditable.  
The following practices apply:

- `meta/study_plan_*.md` explicitly references time and energy constraints  
- `labs/` entries carry timestamps and session type (deep-work, maintenance, learning slot)  
- `reports/` only contain chains that are reproducible inside the defined constraints  
- `psychology/` interprets human factors against these constraints, never as isolated traits

If a planned workstream repeatedly collapses on the same constraint, this is a design flaw in the plan, not a personal failure.  
This repository prefers structural adjustment over blame.


## 7. Ethics and Scope Constraints

All boundaries defined in the root README apply even more strictly here:

- Only authorised scenarios: CTF/lab environments, owned infrastructure, explicit permission  
- No use of psychological models on real persons outside approved scope  
- No documentation that cannot be translated into defensive controls or process change  

Every project must be defensively translatable.  
Constraints define not only *how* work happens here, but also *what* is allowed to exist inside this codebase.
