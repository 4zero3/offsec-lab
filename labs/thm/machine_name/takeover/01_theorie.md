# Theory – Recon Foundations & Variants

## Objective

This document explains the technical foundations of the reconnaissance phase for the target `futurevera.thm`.

The focus is not on tools as an end in themselves, but on the mechanisms that make recon possible in this lab context:
- local name resolution
- HTTP-based virtual host logic
- response comparison
- certificate analysis as a source of additional hostnames

This chapter therefore does not document execution itself.  
It defines the reasoning model on which `02_praxis.md` depends.

---

## Scope

Reconnaissance in this scenario does not begin with blind scanning.  
It begins with reachability, context, and a reliable model of how requests are technically delivered and processed by the server.

Four conditions matter here:
- the target is addressed by domain name
- public DNS resolution is not available
- multiple applications may exist behind the same IP
- status codes alone are not a reliable signal

The consequence is direct:  
Before any meaningful enumeration starts, it must first be understood how name resolution, host selection, and response behavior interact.

---

## Meaning of `MACHINE_IP`

`MACHINE_IP` is a placeholder for the actual IP address assigned to the target machine in the lab.

It is used deliberately in the documentation to keep commands portable and to separate workflow logic from a single concrete instance.

For real execution, the rule is simple:
- in the documentation, `MACHINE_IP` remains as a reusable placeholder
- in the shell, it must be replaced with the real target IP unless a variable is already defined

This placeholder is therefore not cosmetic.  
It is part of reproducibility.

---

## DNS Resolution

DNS determines where traffic is sent.

On Linux systems, host resolution is typically controlled through `/etc/nsswitch.conf`; for `hosts`, a lookup order such as `files dns` is common, which causes local files to be checked before DNS. [web:71][web:84]

In isolated lab environments, internal names such as `futurevera.thm` often do not exist in public or centrally managed DNS.  
Without local mapping, the client cannot translate the target name into an IP address.

That means:
- the browser cannot reach the application
- CLI tools cannot reach the target
- all later HTTP-based analysis fails before the actual request is processed

The first technical requirement is therefore straightforward:  
The target name must be resolvable locally.

### Fast append

```bash
echo "MACHINE_IP futurevera.thm" | sudo tee -a /etc/hosts
```

### Why this matters

This entry does not replace DNS in general.  
It takes precedence in the local resolution order for this specific hostname before DNS is queried, provided DNS remains part of the configured lookup chain. [web:71][web:84]

DNS therefore continues to function for other names. [web:71][web:84]

For the later analysis, the critical point is not **where** name resolution comes from,  
but that `futurevera.thm` resolves deterministically to the correct target IP on the attacking system.

---

## Why name resolution is more than connectivity here

The local host mapping does more than solve a connection problem.  
It creates the condition required to align hostname and target system in a controlled way.

That matters because modern web servers do not always decide only by IP address.  
Several application contexts may exist behind the same destination:
- main website
- development environment
- admin interface
- API
- support or blog application

Which application is returned may therefore depend not only on the destination IP, but also on the requested hostname.

That is why name resolution becomes a prerequisite for virtual host analysis.

---

## HTTP Routing and Virtual Hosts

A single web server can expose multiple applications behind the same IP address.

Separation is often implemented through the HTTP `Host` header.  
The server therefore evaluates not only which IP received the connection, but also which hostname the request is intended for.

This is the basis of VHost enumeration:
- requests go to the same IP
- the hostname is varied deliberately
- response behavior is compared

This is important because the method is not identical to classic DNS subdomain discovery.

DNS discovery asks whether a name resolves officially.  
VHost discovery asks whether the web server behaves differently when a specific hostname is supplied.

A host can therefore be relevant at the application layer even if it does not resolve publicly in DNS.

---

## Signal, not status code

A common mistake in web recon is to treat HTTP status codes as equivalent to usable findings.

A shared status code does not mean that the same application was served.  
A server can respond with `200 OK` to many different hostnames while still returning different content or separate application contexts.

In practice, response size is often the first and most reliable differentiation signal.  
What should be compared includes:
- `Content-Length`
- body byte count
- structure
- consistency
- visible behavior
- deviation from the baseline pattern

Not every response is a signal.  
A signal exists only where observable deviation appears.

---

## Execution variants

This recon model can be applied in several ways.

### 1. Structured approach

The structured approach begins with baseline formation.

Typical order:
1. establish local host mapping
2. observe the baseline behavior of the primary domain
3. build a controlled candidate list
4. compare response behavior
5. validate deviations
6. evaluate secondary artifacts such as certificates

This variant is slower, but methodically cleaner.  
It is well suited for cases where decisions must remain traceable.

### 2. Quick-and-dirty approach

The quick-and-dirty approach reduces preparation and looks for usable deviations early.

Typical characteristics:
- small heuristic candidate list
- fast tests with a changing `Host` header
- focus on visible response differences
- limited preparation, rapid hypothesis building

This variant is useful when time, tooling, or environment are constrained.  
It does not replace validation.

### 3. Certificate-driven approach

The certificate-driven approach uses TLS not only for transport encryption, but also as an information source.

During the TLS handshake, the server presents a certificate.  
Useful hostnames may appear there primarily in SAN entries, and in older or lab-style configurations the Common Name may still carry additional hint value. [web:76][web:82][web:83]

For hostname matching, SAN is treated as the primary source today, while use of the Common Name for that purpose is deprecated under RFC 2818. [web:76][web:79]

As a result, certificate analysis can:
- confirm existing assumptions
- reveal new hostnames
- provide the next enumeration target directly

This method is especially valuable when HTTP-level signals are limited but a valid HTTPS entry point already exists.

---

## Meaning of `XXXX`

`XXXX` marks a redacted or instance-specific component of a discovered hostname in the documentation.

That means:
- the value is not arbitrary
- the value is not generic
- it must not be replaced through guesswork

It must come from actual observation, such as:
- certificate data
- SAN entries
- the Common Name
- headers
- application responses

For reproduction, the rule is therefore clear:  
`XXXX` is not a guessing placeholder.  
It is an abstracted reference to a concrete value that was actually extracted.

---

## Certificate-Driven Discovery

Certificates are not a side detail in this model.

Once a valid VHost or useful HTTPS endpoint has been identified, the certificate may expose information that was not visible at the HTTP layer before.

The technical reason is simple:  
The certificate reveals which hostnames the TLS context is configured to serve; today this information primarily appears in SAN entries and, in older or lab-like configurations, sometimes additionally in the CN. [web:76][web:79][web:82][web:83]

This creates a second information channel alongside classic enumeration:
- HTTP provides behavioral signals
- TLS provides configuration clues

Only the combination of both turns an assumption into a reliable analysis path.

---

## Theoretical core

This chapter is built on four assumptions:

1. Without local name resolution, web-based recon in this type of lab is not reliable.
2. Multiple applications may exist behind the same target IP.
3. The `Host` header may expose different application contexts.
4. Certificates may reveal additional hostnames that wordlist guessing alone does not immediately expose.

The consequence is direct:  
Recon in this scenario is not blind guessing of names.  
It is the controlled comparison of technical reactions to deliberately varied requests.

---

## Transition to practice

The practical phase starts exactly here.

Theory is not repeated there.  
It is operationalized:
- establish host mapping
- generate candidates
- compare responses
- validate deviation
- inspect the certificate
- derive the hidden host

That execution belongs in `02_praxis.md`.  
This chapter defines only the technical foundation that explains why the workflow works.
