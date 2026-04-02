# Results

## Validated Hostnames

The following hostnames were validated during the reconnaissance process:

- `blog.futurevera.thm`
- `support.futurevera.thm`
- `secrethelpdeskXXXX.support.futurevera.thm`

These hostnames did not emerge from a single enumeration step.  
They were identified across different stages of analysis and confirmed through direct technical validation.

---

## Key Finding

A relevant part of the exposed attack surface was not discoverable through initial wordlist-based enumeration alone.

It became visible only after a valid response deviation was identified and the corresponding TLS certificate was inspected.

---

## Confirmed Technical Findings

The following conditions were confirmed during execution:

- multiple virtual host contexts were served behind a shared IP address
- HTTP status codes alone did not distinguish meaningful targets
- most tested hostnames produced uniform fallback-like behavior
- `blog.futurevera.thm` showed a clear behavioral deviation
- certificate data exposed additional hostnames beyond the initial candidate set

These findings show that visibility at the HTTP layer was incomplete without secondary analysis.

---

## Signal Evaluation

Not all observed signals had the same evidential value.

- **Status code** → weak signal; useful for context, not for reliable differentiation
- **Response similarity** → indicator of generic or fallback behavior
- **Response deviation** → primary indicator of a potentially valid VHost
- **Certificate data** → high-value configuration evidence tied to real hostnames

The decisive factor was not that responses existed, but that one response deviated in a meaningful way.

---

## Analytical Outcome

The breakthrough did not come from enumeration volume alone.

It came from a chained interpretation model:
- observe uniform behavior
- identify deviation
- validate the deviating host
- inspect the certificate
- derive the hidden hostname
- verify access

This changed the process from heuristic probing into evidence-based discovery.

---

## Result Significance

Enumeration alone was insufficient to reveal the full structure of the exposed application surface.

Only the combination of:
- behavioral comparison
- targeted validation
- certificate inspection

made the hidden host visible.

The key result is therefore not only that additional hostnames existed.  
The key result is that correct interpretation of system behavior produced the actual discovery signal.
