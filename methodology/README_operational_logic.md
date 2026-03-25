# Methodology

This directory defines the formalised logic of offensive and defensive work in this repository.
It does not document tool collections or isolated tricks, but **traceable decision structures**.

`methodology/` forms the structural layer between raw operational material in `labs/` and condensed reproducibility in `reports/`.
It captures how activity is **observed, classified, linked and acted upon**.

---

# Structural Principle

The methodology is organised into two perspectives on the same operational space:

* `defense/` describes how activity becomes **visible, interpreted and prioritised**
* `offense/` describes how activity is **constructed, chained and advanced**

These perspectives are intentionally mirrored.
They do not represent separate worlds, but two analytical views of the same system dynamics.

---

# Defense

`defense/` defines the logic of **detection, interpretation and escalation**.

* `00_detection_principles.md` – First principles of signal, noise and visibility
* `01_log_sources.md` – Sources of operational visibility
* `02_event_normalization.md` – Converting heterogeneous logs into comparable events
* `03_alert_patterns.md` – Recurring patterns from which actionable alerts emerge
* `04_correlation_logic.md` – Linking multiple signals into meaningful incidents
* `05_soc_triage_logic.md` – Human decision logic for classification and escalation
* `06_detection_failures.md` – Structural failure points of defensive visibility

The defensive perspective asks:

*What becomes visible, how is it interpreted, and where does detection fail?*


---

# Offense

`offense/` defines the logic of **approach, chaining and operational advancement**.

* `00_attack_flow_principles.md` – First principles of offensive flow structure
* `01_enumeration_principles.md` – Information acquisition as the basis of every chain
* `02_attack_chain_logic.md` – How isolated observations become viable attack chains
* `03_privilege_escalation_logic.md` – Transition to higher impact through local escalation
* `04_post_exploitation_decisions.md` – Decision paths after access, success or dead end

The offensive perspective asks:

*What is discovered, how does it become usable, and how does it evolve into a durable chain?*

---

# Mirrored Layers

Both sections follow the same conceptual layers:

| Level | Defense                | Offense                     |
|------|------------------------|-----------------------------|
| 00   | Detection Principles   | Attack Flow Principles      |
| 01   | Log Sources            | Enumeration Principles      |
| 02   | Event Normalization    | Attack Chain Logic          |
| 03   | Alert Patterns         | Privilege Escalation Logic  |
| 04   | Correlation Logic      | Post-Exploitation Decisions |
| 05   | SOC Triage Logic       | —                           |
| 06   | Detection Failures     | —                           |

This mirroring is intentional.
It highlights that defense and offense are **different decision systems operating within the same environment**.

---

# Boundary

`methodology/` is not:

* a collection of ready-made exploits
* a command cheat sheet
* a dump of walkthroughs or course material

If content only describes **what happened**, it belongs in `labs/`.
If it explains **why decisions were taken and how they become reproducible**, it belongs in `methodology/`.

---

# Repository Role

`methodology/` connects several other layers of the repository:

* `philosophy/` – abstract thinking models
* `psychology/` – human decision and context factors
* `labs/` – raw observations, tests and dead ends
* `case_studies/` – condensed and reproducible results

This makes `methodology/` the layer in which **observation becomes durable structure**.

---

# Key Principle

The quality of offensive or defensive work is not primarily visible in the outcome, but in the **structure of the decisions**.

`methodology/` exists to make that structure **explicit, auditable and repeatable**.
