---
uri: odd://canon/constraints/overlay-extends-core
kind: canon
title: "Overlay Extends Core — Complement by Default, Supersede on Conflict"
audience: canon
exposure: nav
tier: 2
voice: neutral
stability: experimental
tags: ["constraint", "overlay", "core", "federation", "complement", "supersede", "cascade"]
epoch: E0010
date: 2026-06-10
derives_from: "odd://canon/constraints/core-boundary-criteria, odd://canon/principles/knowledge-base-as-the-unit"
governs: "The relationship between a core document and an overlay document that extends it, in federated ODD knowledge bases"
provenance: "Maintainer ruling, live adjudication 2026-06-10"
---

# Overlay Extends Core — Complement by Default, Supersede on Conflict

> When an overlay knowledge base extends a core document, the default relationship is complement: both documents load, both remain available to readers and tools, and the overlay adds to the core rather than replacing it. Where the two genuinely conflict — contradictory instructions, incompatible defaults — the overlay supersedes the core for that instance and scope, because the overlay is the operator's adjudication of the portable rule for their context. The tie-break is explicit and deliberately conservative: if it is unclear at the clause level whether the overlay clause complements or conflicts with the corresponding core clause, treat the overlay clause as superseding that core clause only — the rest of the core document still loads and remains authoritative. Closest prior art is the CSS cascade (general rules inherited, specific rules win on conflict); the distinction is that this operates at document scope with an explicit confusion tie-break, because an agent reading two contradictory laws and guessing is worse than an agent reading one. Experimental: minted from a single live ruling, untested against a completed split; the first two applications (stakes-calibration, AGENTS.md) are the validation cases.

---

## Summary — Both Load, Overlay Adds, Conflict Resolves Downward to the Overlay

Federation creates a layering question the boundary criteria deliberately left open: a portable core rule and an instance overlay that extends it must coexist in the same read scope. The ruling: complement is the default posture — the overlay is additive, the core stays authoritative for everything it says that the overlay does not contradict, and tools surface both. Supersession is the exception, triggered only by genuine conflict, and scoped to the conflicting instance — the overlay never silently retires the rest of the core document. The confusion clause exists because the cost asymmetry is real: wrongly treating complements as superseding loses some core guidance temporarily; wrongly treating conflicts as complementary hands an agent two contradictory laws at once. When in doubt about a specific clause, the overlay clause wins for that clause only and the doubt gets journaled for the maintainer.

## Application Discipline

- An overlay that extends a core doc declares it (`extends:` or `derives_from:` referencing the core URI), so the relationship is machine-visible.
- Conflict is judged clause by clause, not document by document; supersession is scoped to the conflicting clause.
- Every invocation of the confusion tie-break is a journal entry — repeated confusion on the same pair is a signal the core doc or the overlay needs rewriting, not re-ruling.

## Retraction Conditions

- Revise if the first two splits (stakes-calibration, AGENTS.md) show the clause-level supersession is unworkable in practice — fall back to document-level supersession.
- Retract the confusion tie-break if journals show it being invoked routinely rather than exceptionally; routine confusion means the model is wrong, not the readers.
