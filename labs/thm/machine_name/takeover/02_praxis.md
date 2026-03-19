# Praxis – Actual Execution (Real Scenario)

## Initial Situation

Target: `futurevera.thm`

The lab environment did not provide public DNS resolution.  
At the same time, the system was mid-upgrade, which caused two practical constraints:

- SecLists were not available
- package installation was blocked

This forced a deviation from the planned workflow.

---

## Step 1 – DNS Baseline

The first step was to establish local name resolution.

Command used:

echo "MACHINE_IP futurevera.thm" | sudo tee -a /etc/hosts

Result:

The domain could now be resolved locally.  
Without this step, no HTTP-based interaction would have been possible.

---

## Step 2 – Adapting to Constraints

The original plan was to use a large wordlist for VHost enumeration.

This was not possible due to missing SecLists and blocked installation.

Decision:

Instead of stopping, a reduced manual candidate list was created.

This was not a fallback in terms of logic, only in terms of scale.

---

## Step 3 – Manual Candidate List

A small heuristic list was used:

www, dev, test, admin, portal, blog, support, api, staging

Goal:

Cover common naming patterns quickly to generate initial signals.

---

## Step 4 – VHost Enumeration

Enumeration was performed via Host header manipulation using ffuf.

Observation:

All responses returned HTTP status 200.

Interpretation:

Status code alone was not usable as a signal in this scenario.

---

## Step 5 – Behavioral Analysis

Since status codes were uniform, analysis shifted to response behavior.

Focus:

- response size
- consistency across requests

Result:

Most candidates produced identical responses.  
One exception was observed:

blog showed a clear deviation.

Decision:

blog.futurevera.thm was treated as a valid VHost candidate.

This decision was based on behavior, not on tool output.

---

## Step 6 – Verification

The identified host was mapped locally.

echo "MACHINE_IP blog.futurevera.thm" | sudo tee -a /etc/hosts

Result:

Access confirmed.

This indicated that blog was served as a separate application context.

---

## Step 7 – TLS Certificate Analysis

The next step was to extract certificate information from the validated host.

openssl s_client -connect blog.futurevera.thm:443 | openssl x509 -noout -text | grep DNS

Result:

The certificate revealed additional hostnames via SAN entries:

- support.futurevera.thm
- secrethelpdeskXXXX.support.futurevera.thm

Interpretation:

These hostnames were part of the real configuration but not visible through enumeration.

---

## Step 8 – Final Verification

The hidden hostname was added to the hosts file.

echo "MACHINE_IP secrethelpdeskXXXX.support.futurevera.thm" | sudo tee -a /etc/hosts

Result:

The application became accessible via browser.  
The flag was retrieved.

---

## Actual Analysis Path

The decisive sequence was:

Response deviation  
→ hypothesis  
→ validation  
→ certificate extraction  
→ hidden hostname  
→ access

This path is reproducible and independent of specific tooling.