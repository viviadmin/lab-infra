# Architecture Decision Records

This file records every significant architecture decision in the lab — what
was chosen, what was rejected, and the constraint that drove the choice. New
decisions are appended; earlier ones are never edited (superseded, not
deleted). The chain is the story.

Format adapted from Michael Nygard's lightweight ADR template.

---

## ADR-001: No Proxmox — two-node lab on constrained hardware

**Date:** 2026-11-02
**Status:** Accepted

**Context:** Lab hardware is a Raspberry Pi 3 (1 GB RAM, USB SSD) and a single
RHEL 10 VM on the local machine. No spare hardware, no budget for a hypervisor
host. Kubernetes will not run on the Pi (1 GB RAM is insufficient).

**Decision:** Skip Proxmox entirely. Use the local hypervisor's snapshots as
the rollback mechanism. Kubernetes practice goes to `kind` locally or a free
cloud VM, not the Pi.

**Consequences:**
- Simpler lab, faster setup, no idle hardware
- No hands-on Proxmox experience — acceptable, since the transferable skill is
  automating VM creation, not a specific hypervisor product
- Snapshot discipline becomes mandatory: the VM's saved state is the only
  rollback path
- K8s stays off the Pi; `kind` is the K8s surface

**Revisit when:** a mini PC becomes available (≥16 GB RAM) or a target job
requires Proxmox specifically.