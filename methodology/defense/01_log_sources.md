# Defense: Log Sources

This chapter describes the primary sources of usable telemetry for detection.  
It follows directly after `00_detection_principles.md` and precedes `02_alert_patterns.md`.

Log sources are not the data itself, but the **sources from which visibility emerges**.  
Without these sources, detection theory remains without operational basis.

This chapter is not intended as a tool list or SIEM configuration guide.  
It is intended as a **coverage model**: which sources are essential for which attack phases, and where their limits are.

---

## 1. The 4 Pillars of Telemetry

Log sources are grouped by their **observation layer**.  
Each layer covers different attack phases and techniques.

### 1.1 Endpoint Telemetry

**What:** Process/file/registry/network activity on endpoints.  
**Value:** Visibility into code execution, persistence, credential abuse, lateral movement.  
**Sources:** EDR agents (Sysmon, Defender, CrowdStrike), OS events (Windows Security, Linux Audit).  
**Blind Spot:** Headless/cloud workloads without agents.

### 1.2 Network Telemetry

**What:** Communication between systems (IP, port, protocol, payload metadata).  
**Value:** Visibility into initial access, C2, exfiltration, scanning.  
**Sources:** NetFlow, proxy logs, DNS, firewall/IDS, NDR.  
**Blind Spot:** Encrypted traffic without inspection or metadata strategy.

### 1.3 Identity Telemetry

**What:** Authentication, permissions, group memberships.  
**Value:** Visibility into privilege escalation, credential theft, account abuse.  
**Sources:** AD audit logs, Kerberos events, IAM logs (Azure AD, Okta), VPN logins.  
**Blind Spot:** Service accounts, token abuse, pass-the-hash without correlation.

### 1.4 Cloud / Control Plane Telemetry

**What:** API calls, IAM changes, storage access, compute events.  
**Value:** Visibility into cloud-native attacks, misconfigurations, lateral movement.  
**Sources:** CloudTrail (AWS), Azure Monitor, GCP audit logs, Kubernetes audit logs.  
**Blind Spot:** Serverless without logging, incomplete audit trails.

---

## 2. Coverage Matrix – Which Source Covers What?

| Attack Phase | Endpoint | Network | Identity | Cloud |
|--------------|----------|---------|----------|-------|
| Recon | - | DNS, scanning | - | - |
| Initial Access | Phishing, exploit artefacts | C2, exploit, inbound traffic | VPN logins | IAM abuse |
| Execution | Process creation | - | - | Lambda / function execution |
| Persistence | Registry, services, scheduled tasks | - | Service accounts | IAM roles |
| PrivEsc | SUID, tokens, local abuse | - | Group changes | IAM escalation |
| Lateral Movement | SMB, RDP, WinRM | NetFlow, east-west traffic | Kerberos | Cross-account activity |
| Exfiltration | File access | DNS tunneling, egress traffic | - | S3 / storage access |

**Rule:** As a rule, each phase should be covered by at least two independent sources for robust detection.

---

## 3. Source Prioritisation

Not all logs have the same value.  
Prioritisation follows **signal/noise ratio**, **coverage gap** and **correlation depth**.

### Priority 1 – Essential

- Windows Security Logs (4624/4625/4672/4673)
- Sysmon or equivalent endpoint process telemetry
- proxy/DNS logs
- AD audit logs

### Priority 2 – High Value

- firewall/NetFlow
- EDR behavioural logs
- CloudTrail/IAM logs
- VPN and MFA events

### Priority 3 – Supplementary

- application logs
- WAF logs
- mobile device logs
- database / SaaS logs

---

## 4. Common Coverage Gaps

The largest blind spots in log coverage:

### 4.1 Missing Endpoint Visibility

- IoT/OT devices without agents
- legacy Windows systems without Sysmon
- headless servers without EDR

### 4.2 Encrypted Traffic

- HTTPS without proxy inspection
- TLS C2 without metadata analysis

### 4.3 Identity Blind Spots

- service accounts without audit
- token abuse without host correlation
- pass-the-hash without network correlation

### 4.4 Cloud Misconfigurations

- serverless without logging
- IAM changes without alerting
- audit trails only partially enabled

---

## 5. Integration into the Detection Pipeline

Log sources are the input for the following pipeline:

```text
Log Sources → Normalization → Correlation → Alert Patterns → Triage / Escalation
```

Detection quality therefore depends not only on the source itself, but also on how that source is processed.

- Without normalization, sources collapse into isolated events
- Without correlation, visibility remains fragmented
- Without retention, the timeline breaks
- Without context, even good telemetry remains operationally weak

`01_log_sources.md` therefore does not end with the question of what is collected.  
It leads directly to the question of how durable patterns emerge from it.

---

## 6. Boundary of This Chapter

This chapter does not cover:

- concrete Sigma rules
- SPL/KQL queries
- SIEM onboarding processes
- product-specific parsers

Those follow later from the structure.  
`01_log_sources.md` defines the **visibility base**, not the finished detection.

---

## Key Principle

Log sources are not merely technical inputs.  
They define the boundaries of what a defensive system is capable of knowing.

Detection quality is therefore already constrained before alerting begins.  
A weak visibility layer cannot later be repaired by better rules alone.
