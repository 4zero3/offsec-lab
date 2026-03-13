# Methodology

This directory defines the formalised logic of offensive and defensive work in this repository.  
It does not document tool collections or isolated tricks, but traceable decision structures.

`methodology/` is the layer between raw material in `labs/` and condensed reproducibility in `reports/`.  
It captures how activity is observed, classified, linked and acted upon.

---

## Structural Principle

The methodology is divided into two perspectives on the same operational space:

- `defense/` describes how activity becomes visible, interpreted and prioritised  
- `offensive/` describes how activity is built, chained and advanced  

Both sections are intentionally mirrored.  
They do not represent separate worlds, but two views of the same system dynamic.

---

## Defense

`defense/` defines the logic of detection, assessment and escalation.

- `00_detection_principles.md` – First principles of signal, noise and visibility  
- `01_log_sources.md` – Sources of operational visibility  
- `02_alert_patterns.md` – Recurring patterns from which actionable alerts emerge  
- `03_triage_and_escalation_logic.md` – Decision logic between classification, handoff and escalation  
- `04_detection_failures.md` – Typical failure points of defensive visibility

The defensive side asks:  
What becomes visible, how is it interpreted, and where does detection fail?

---

## Offensive

`offensive/` defines the logic of approach, chaining and escalation.

- `00_attack_flow_principles.md` – First principles of offensive flow structure  
- `01_enumeration_principles.md` – Information acquisition as the basis of every chain  
- `02_attack_chain_logic.md` – How isolated observations become viable attack chains  
- `03_privilege_escalation_logic.md` – Transition into higher impact through local escalation  
- `04_post_exploitation_decisions.md` – Decisions after success, access or dead end

The offensive side asks:  
What is discovered, how does it become usable, and how does it become a durable chain?

---

## Mirrored Layers

Both subtrees follow the same internal logic:

| Level | Defense | Offense |
|------|---------|---------|
| 00 | Detection Principles | Attack Flow Principles |
| 01 | Log Sources | Enumeration Principles |
| 02 | Alert Patterns | Attack Chain Logic |
| 03 | Triage and Escalation Logic | Privilege Escalation Logic |
| 04 | Detection Failures | Post-Exploitation Decisions |

This mirroring is intentional.  
It makes visible that defense and offense are different decision systems inside the same operational space.

---

## Boundary

`methodology/` is not:

- a collection of ready-made exploits  
- a command cheatsheet  
- a dump of walkthroughs or course material  

If content only describes *what* was done, it belongs more naturally in `labs/`.  
If it explains *why* a decision was taken and *how* it becomes reproducible, it belongs in `methodology/`.

---

## Repository Role

`methodology/` connects several other parts of the repository:

- `philosophy/` provides the abstract model of thinking  
- `psychology/` adds human decision and context factors  
- `labs/` provides raw material, tests, dead ends and observations  
- `reports/` compresses outcomes into reproducible final form  

This makes `methodology/` the area in which observation becomes durable structure.

---

## Key Principle

The quality of offensive or defensive work is not first visible in the outcome, but in the structure of the decisions.  
`methodology/` exists to make that structure explicit, auditable and repeatable.
