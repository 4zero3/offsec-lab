# Theory – Recon Foundations & Variants

## Objective

This document explains the underlying mechanics behind the reconnaissance process.

It also includes multiple execution strategies:
- structured approach
- quick & dirty approach
- certificate-driven approach

---

## DNS Resolution

DNS determines where traffic is sent.

In lab environments:
- no public DNS resolution exists
- manual mapping is required

Options:

### Fast append
```bash
echo "MACHINE_IP futurevera.thm" | sudo tee -a /etc/hosts
