# Meta: Personal Rules – Operating System for Offensive Work

This document defines non-negotiable rules governing all activities in this repository.  
Personal Rules are not motivational advice – they are **hard operational law**.

Their purpose: Eliminate decision ambiguity and prevent **Attentional Collapse** during offensive work.

---

## 1. Invariants – Never Negotiable

- **No half-baked exploits**  
  No attack steps started outside defined focus slots.

- **Chain-of-Reasoning-Historie (CoRH) mandatory**  
  Every step documented as: **Hypothesis → Observation → Decision → Next step**

- **Energy Threshold enforced**  
  Reasoning loop or focus <10 minutes = immediate session downgrade.

- **Defensive Translatability**  
  Every exploit or attack chain must translate to a **control, detection or training improvement**.

Violation of invariants results in a **24h repository lock**.

---

## 2. Session Rules – Protocolled Flows

### Session Start
[YYYY-MM-DD HH:MM]
Session: [Deep-Work | Maintenance | Learning]
Energy: [High | Medium | Low]
Context: [Mode A | Mode B | Mode C]
Current Hypothesis: [One sentence]


### Session End (State Capture)
CoRH Snapshot:
Hypothesis: [current]
Observation: [what was found]
Decision: [why this path was chosen]
Next Step: [concrete next attack point]
Open: [dead ends, open questions]


This guarantees resumability even after long interruptions.

---

## 3. Decision Rules – Automated Choice

| Situation | Decision Rule |
|-----------|---------------|
| High/Critical alert or uncertainty | Immediate L2 escalation |
| L2 offline >30min (Critical) | Call L2 → L3 → Manager |
| Compromised communication channel | Phone only, never chat |
| Energy below threshold | Downgrade to repository maintenance |
| Monolithic 10h session required | Break chain into 90min segments |

---

## 4. Documentation Rules – Audit Trail

- **labs/**: Raw data, timestamps and session type  
- **methodology/**: Generalizable logic, tool-agnostic principles  
- **reports/**: Only reproducible chains within defined constraints  

All documentation must include:
- CoRH structure  
- Defensive derivation (attack → prevention/detection)

---

## 5. Anti-Burnout Protocol

- Maximum **2 Deep-Work slots back-to-back (≈180 minutes)**  
- After critical failure: **24h No-Offsec rule**  
- Weekly review: *What did not work and why?*  
- Recovery Mode C activated: `labs/` cleanup only, no new hypotheses

---

## 6. Enforcement Mechanism

### Automated Checks (pre-commit)
- CoRH structure present in new files  
- Session timestamps documented  
- Energy threshold recorded  
- Defensive translatability visible

### Manual Audit (weekly)
- Were sessions within defined constraints?  
- Are there incomplete attack chains?  
- Were invariants violated?

Repeated violations result in a **72h repository lock**.

---

## Key Principle

Personal Rules eliminate willpower decisions in critical moments.  

**Attentional Collapse occurs exactly when discipline fails.**

This is not perfectionism.  
This is **Operational Reliability**.
