---
status: candidate
pending: captain-ratification
provenance: "captain's log 2026-07-18 ~12:10 EDT (Bee capture), relayed via Otto seat sess_f7294064"
title: "Policies vs. Requirements — A Category the Program Has Been Collapsing"
tags: ["policy", "requirements", "steering", "prd", "candidate-seed"]
---

# Policies vs. Requirements — A Category the Program Has Been Collapsing

> "Policy" has been used to name two different things: durable, slow-changing principles (POLICIES) and fast-changing, build-specific functional needs (REQUIREMENTS). Collapsing them is a suspected root cause of steering failures — requirements dressed as policy resist necessary change, and policy dressed as requirements churns when it shouldn't.

---

## Summary — Two Artifact Types Have Been Sharing One Name

The program has overloaded the word "policy" to cover everything that shapes AI behavior, from durable abstract guidance down to the specific functional needs of a single build. This seed, crediting an observation from Jessica, proposes splitting the category in two:

- **POLICIES** — principles and abstract guidance. Durable, slow-changing, canon-shaped.
- **REQUIREMENTS** — specific functional needs of a build. Fast-changing, PRD-shaped.

Lumping the two together is a suspected root cause of steering failures observed in the wild: a requirement written as if it were policy becomes artificially resistant to change (it inherits policy's durability expectations when it should be revisable per build), and a policy written as if it were a requirement churns on every build cycle (it inherits requirements' fast-changing cadence when it should be stable).

The candidate implication: mode-output contracts and the PRD gate should each name explicitly which artifact type — policy or requirement — they are demanding, rather than leaving "policy" to do double duty.

---

## Open Question for Ratification

The exact boundary test for classifying an existing document as policy vs. requirement, and the migration path for documents currently filed as "policy" that are actually requirements (or vice versa), are not yet defined. This seed names the split; it does not resolve the boundary test or the migration plan.
