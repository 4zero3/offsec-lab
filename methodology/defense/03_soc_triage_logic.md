# SOC L1 Core Skills: Reporting, Escalation, Communication

**Author:** 4zero3  
**Date:** 2026-03-10  

## Executive Summary

This note documents three core L1 SOC competencies observed during THM triage practice: **reporting, escalation and communication**.  
The goal is to preserve analysis context, ensure proper threat handling and maintain operational coordination inside the SOC.

---

## 1. Alert Reporting

**Purpose:**  
Provide detailed True Positive (TP) documentation before L2 handoff. This preserves context and saves analysis time.

**Why:**  
L2 analysts require initial context to avoid starting investigations from scratch.

**How:**  
Use the **5Ws framework** (Who, What, When, Where, Why) combined with evidence such as logs or screenshots.

### Reporting Template

```
Status: Closed | Severity: High | Verdict: TP | Assignee: L2

Comment
Timeline:
Indicators:
Analysis:
Actions Taken:
Escalation Reason:
```

### Example (Phishing)
09:12 UTC – Attachment REPORT.rar delivered via email.
SPF validation failed.
Verdict: True Positive.
Escalation: Malware analysis required.



---

## 2. Alert Escalation

**Trigger:**  
True Positives that require deeper investigation, for example:

- Malware analysis
- Lateral movement
- Persistence mechanisms
- Privilege escalation activity

**Process:**

1. Complete L1 triage and reporting
2. Attach relevant logs and evidence
3. Assign ticket to L2 analyst

**Benefit:**  
L2 inherits full context and can continue analysis without repeating triage work.

**Operational Rule**

High or Critical severity alerts — or any situation involving uncertainty — must be escalated to **L2**.

---

## 3. Communication Scenarios

| Scenario | Action |
|--------|--------|
| L2 offline (Critical, 30min no reply) | Use emergency contacts: Call L2 → L3 → Manager |
| Slack/Teams compromise | Do **not** use compromised chat – phone communication only |
| Alert flood (including critical alerts) | Prioritize workflow and notify L2 immediately |
| Late misclassification detected | Immediate escalation to L2 (potential dwell time risk) |
| Unsearchable SIEM logs | Perform partial triage and escalate to L2 or engineering |

---

## Key Takeaway

Reporting preserves investigative context.  
Escalation ensures threats are properly analyzed.  
Communication keeps the SOC aligned across analysts and departments.