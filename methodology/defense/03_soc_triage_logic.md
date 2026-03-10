SOC L1 Core Skills: Reporting, Escalation, Communication

Author: 4zero3
Date: March 10, 2026
Location: Munich, Germany

Executive Summary
Three core L1 competencies from today's THM SOC triage: Reporting (L2 context), Escalation (threat resolution), Communication (coordination). Production-ready framework.

1. Alert Reporting
Purpose: Detailed TP documentation before L2 handoff. Saves analysis time.
Why: L2 needs initial context - eliminates starting from scratch.
How: 5Ws + evidence (logs/screenshots).

My Template (battle-tested):

Status: Closed | Severity: High | Verdict: TP | Assignee: L2
Comment: [Timeline/Indicators/Analysis/Actions/Escalation Reason]
............................................................................
Example (Phishing):
"09:12 UTC REPORT.rar delivered – SPF Fail. TP. Escalate: Malware analysis."


2. Alert Escalation
Trigger: TPs requiring deeper analysis (malware, lateral movement).
Process: Assign + attach report.
Benefit: L2 inherits full context.

My Rule: High/Critical or uncertainty → Always L2.


3. Communication Scenarios

Scenario                                    	Action

L2 offline (Critical, 30min no reply)	        Emergency contacts: Call L2 → L3 → Manager
Slack/Teams compromise	                        Never use compromised chat - Phone only
Alert flood (criticals included)	            Workflow prioritization + Notify L2
Late misclassification	                        Immediate L2 - Dwell risk (weeks!)
Unsearchable SIEM logs	                        Partial triage + Escalate to L2/Engineer

Key Takeaway
Reporting preserves context. Escalation resolves threats. Communication coordinates SOC → departments.