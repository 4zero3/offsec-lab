# Results

## Validated Hostnames

- blog.futurevera.thm
- support.futurevera.thm
- secrethelpdeskXXXX.support.futurevera.thm

---

## Key Finding

A relevant portion of the attack surface was not discoverable through wordlist-based enumeration.

It was exposed through TLS certificate metadata.

---

## Technical Breakdown

The environment showed the following characteristics:

- multiple virtual hosts shared a single IP address
- HTTP responses were intentionally uniform
- status codes did not differentiate between valid and invalid hosts
- certificate SAN entries exposed additional infrastructure

---

## Root Cause

The exposure resulted from a combination of factors:

- shared infrastructure without strict separation
- generic response behavior masking internal structure
- certificates containing additional hostnames
- lack of alignment between visible and actual assets

---

## Signal Analysis

Different types of signals were observed and evaluated:

Status Code  
→ weak signal, not reliable in isolation

Response Similarity  
→ indicates noise or default behavior

Response Deviation  
→ primary indicator of valid targets

Certificate Data  
→ high-value source of real configuration data

---

## Critical Insight

The breakthrough did not come from enumeration itself.

It came from interpreting deviations in behavior and validating them through TLS data.

---

## Conclusion

Enumeration alone was insufficient to reveal the full structure.

Only the combination of:

- behavioral analysis  
- hypothesis-driven validation  
- certificate inspection  

made the hidden attack surface visible.

The key factor was not tool execution, but correct interpretation of system behavior.