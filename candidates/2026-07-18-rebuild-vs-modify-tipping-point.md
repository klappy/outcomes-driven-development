---
status: ratified
ratified_by: "captain, in-session 2026-07-19"
provenance: "captain's log 2026-07-18 ~12:10 EDT (Bee capture), relayed via Otto seat sess_f7294064"
title: "The Rebuild-vs-Modify Tipping Point — Naming What 'Technical Debt' No Longer Names"
tags: ["rebuild", "technical-debt", "layering", "candidate-seed"]
---

# The Rebuild-vs-Modify Tipping Point — Naming What "Technical Debt" No Longer Names

> "Technical debt" is the wrong term for the AI-era version of this decision, and teams misread it as a result. Under agentic coding the old 80/20 completion curve became 99/1 — a near-complete one-shot whose last 1% costs more than the first 99 did (and the 99% itself may be perceived rather than real). The standing method is "bulldoze the house, keep the blueprint": rebuilding is cheap if the blueprint — requirements and policies, properly split — is good. What is missing is a named metric for when to bulldoze a layer versus modify it in place, plus the rule that layers are rebuilt one at a time, never the whole stack at once.

---

## Summary — A Named Threshold Is Missing, Not the Instinct to Rebuild

Agentic coding changed the shape of the completion curve. The old rule of thumb — 80% of the work is fast, the last 20% is disproportionately expensive — has become 99/1: a near-complete one-shot generation whose final 1% costs more effort to finish than the first 99% did. The 99% figure may itself be a perception rather than a measured reality, which matters for how much weight it should carry.

Calling this situation "technical debt" misleads teams into treating it as a financing decision (pay it down incrementally) when the more effective move is often structural replacement. The standing method for handling it is "bulldoze the house, keep the blueprint" — full rebuild of a layer is cheap and low-risk if the blueprint (the requirements and policies that describe what the layer must do, properly separated per the policies-vs-requirements split) is sound.

What this seed identifies as missing is not the rebuild instinct itself, but a **named metric or threshold** for deciding when a layer has crossed into bulldoze territory versus when it should simply be modified in place — and the accompanying rule that rebuilding happens **one layer at a time** (the "vodka" principle: each layer does exactly one thing), never the whole stack simultaneously.

Evidence cited in the wild: OddKit — thin, single-purpose — has needed no meaningful modification in months. ARS — thick, multi-purpose — hit a 2.8-day outage and is now being subtractively thinned as a corrective response.

---

## Open Question for Ratification

Neither the term to replace "technical debt" nor the threshold's operational test (what specifically triggers "bulldoze this layer" versus "modify in place") has been defined. This seed names the gap and the supporting evidence; it does not propose the metric itself.
