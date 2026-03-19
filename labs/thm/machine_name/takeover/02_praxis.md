# Praxis – Recon Execution (Real Scenario_thm)

## Initial Situation

**Target:** `futurevera.thm`

**Constraints:**
- System upgrade in progress
- SecLists not available
- Package installation blocked

The originally planned full wordlist-based enumeration could not be executed.

**Decision:** Do not wait. Adapt the method to the environment.

## Notes

**MACHINE_IP** is used as a placeholder for the actual IP address of the target machine assigned in the lab environment.  
It is kept in the commands to make the workflow reusable and easier to document.  
Before execution, replace `MACHINE_IP` with the real target IP if required.

**XXXX** indicates a redacted or variable part of the discovered hostname.  
It is used here intentionally to avoid hardcoding or disclosing the full value in the write-up.  
During the actual attack path, this segment must be taken exactly as observed in the certificate output.

---

## Step 1 – Local DNS Baseline

Before any HTTP-based interaction, the domain must resolve locally.

```bash
echo "MACHINE_IP futurevera.thm" | sudo tee -a /etc/hosts
```

**Result:**
- Browser and CLI tools can route requests
- HTTP layer becomes reachable

> Without this step, all further actions fail at name resolution.

---

## Step 2 – Adapting to Constraints

A full-scale enumeration using large wordlists (e.g. SecLists) was not possible.
Instead of treating this as a blocker, the approach was reduced to a controlled heuristic method.

**Goal:**
- Generate initial signals
- Establish observable behavior
- Enable comparison

---

## Step 3 – Manual Candidate List (Heuristic Enumeration)

A small, manually defined list of common subdomain patterns was created:

```
www
dev
test
admin
portal
blog
support
api
staging
```

### Why These Names

These are not random guesses. They are derived from common real-world infrastructure patterns:

| Candidate | Rationale |
|-----------|-----------|
| `www` | Default web entrypoint |
| `dev`, `test`, `staging` | Development environments often exposed unintentionally |
| `admin`, `portal` | Internal or administrative interfaces |
| `api` | Backend communication endpoints |
| `blog`, `support` | Frequently separated applications |

> Organizations tend to reuse predictable naming conventions across environments.

### Technical Principle

This step does **NOT** rely on DNS resolution. It relies on **HTTP routing behavior**:
- All requests are sent to the same IP
- The `Host` header determines which application is served

**Meaning:** Even if a subdomain does not exist in DNS, the backend can still respond if the `Host` header matches a configured VHost.

### Objective

The goal is **NOT** full discovery. The goal is:
- Establish a baseline response
- Generate comparable samples
- Detect deviations

This step creates the **first signal layer** for further analysis.

### Expected Outcome

One of two situations:

1. **All responses behave identically** → indicates generic fallback behavior
2. **One or more responses differ** in size, structure, or response pattern → indicates a **valid VHost candidate**

### Decision Logic

Relevance is determined by **deviation** — not by:
- Status code alone
- Number of responses

But by:
- Observable difference compared to baseline

---

## Step 4 – VHost Enumeration

```bash
ffuf -u https://MACHINE_IP \
     -w vhosts.txt \
     -H "Host: FUZZ.futurevera.thm"
```

**Observation:** All responses returned HTTP `200` — no differentiation via status code.

**Conclusion:** Status code alone is **not** a reliable signal.

---

## Step 5 – Behavioral Analysis (Critical Step)

Responses were compared based on:
- Response size
- Consistency

**Result:** Most candidates produced identical responses — `blog` showed a **clear deviation**.

**Interpretation:** `blog` is not part of the generic fallback behavior.

---

## Step 6 – Validation of Candidate

```bash
echo "MACHINE_IP blog.futurevera.thm" | sudo tee -a /etc/hosts
```

**Result:**
- Access confirmed
- Separate application context identified

> At this point: A valid VHost entry point exists.

---

## Step 7 – TLS Certificate Analysis

```bash
openssl s_client -connect blog.futurevera.thm:443 </dev/null 2>/dev/null \
  | openssl x509 -noout -text \
  | grep DNS:
```

**Result:**
```
DNS:support.futurevera.thm
DNS:secrethelpdeskXXXX.support.futurevera.thm
```

### Why This Works

During the TLS handshake:
- The server presents its certificate
- The certificate contains **SAN entries**
- SAN entries list **configured hostnames**

> This is not guessing. This is **extracting configuration data**.

### Why This Step Only Works Now

Earlier attempts failed because:
- No valid VHost context existed
- Certificate could not be mapped correctly
- Wrong entry point

Now: **valid VHost → correct certificate → usable data**

---

## Step 8 – Final Verification

```bash
echo "MACHINE_IP secrethelpdeskXXXX.support.futurevera.thm" | sudo tee -a /etc/hosts
```

**Browser access:** Hidden application is served — **flag is visible.**

---

## Final Analysis Path

```
constrained environment
  → heuristic candidate generation
    → uniform responses observed
      → deviation identified (blog)
        → VHost validated
          → certificate extracted
            → hidden hostname revealed
              → access achieved
```

---

## Core Insight

Enumeration alone did not reveal the target.

The decisive factor was:

> **Response deviation → Certificate analysis → Hidden host discovery**

---

## Key Learning

> Same status code does **NOT** mean same behavior.
> Only **deviation** creates signal.
