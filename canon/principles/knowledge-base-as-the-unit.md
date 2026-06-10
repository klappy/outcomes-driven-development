---
uri: odd://canon/principles/knowledge-base-as-the-unit
kind: canon
title: "Knowledge Base as the Unit — Everything Else Is a Projection"
audience: canon
exposure: nav
tier: 1
voice: neutral
stability: draft
tags: ["principle", "knowledge-base", "projection", "cqrs", "artifacts", "directors-chair", "substrate", "organizing-unit"]
relevance: decision
execution_posture: governing
date: 2026-06-09
derives_from: "odd/decisions/D0002 (canon storage model), canon/principles/scoped-truth.md, canon/principles/vodka-architecture.md, canon/decisions/models-do-not-mutate-canon.md"
complements: "odd://canon/constraints/core-boundary-criteria, klappy://writings/artifacts-are-projections (public companion essay, artifact-side telling)"
governs: "The organizing unit of a program: what is durable (the knowledge base), what is derived (every artifact), and the contract a projector must honor"
---

# Knowledge Base as the Unit — Everything Else Is a Projection

> A program organizes around its knowledge base, not its artifacts. The knowledge base is the only durable asset: the encoded expertise, governance, and decisions of its maintainer. Everything downstream — code, sites, documents, audio, images, video, applications — is a projection: a view materialized from the knowledge base by a projector, deterministic or generative, and regenerable at will. Artifacts were already declared ephemeral; this principle states why ephemerality is safe: anything projected can be re-projected. The human's seat is the director's chair — adjudicating what enters the canon and directing which projections get made.

## Summary — One Question Decides Everything: Which Knowledge Base Owns This Truth?

When the knowledge base is the unit, every other organizational question collapses into one: *which knowledge base owns this truth?* Small projects answer it trivially — the code base and the knowledge base are the same repository, because the knowledge is about that project. Larger programs federate: a portable core, personal or instance overlays, tool manuals — each a knowledge base with one concern (routing governed by `odd://canon/constraints/core-boundary-criteria`). A repository serving several concerns at once is not a bigger knowledge base; it is several knowledge bases tangled, and the tangle taxes every downstream projection.

In the storage model's terms (D0002): the knowledge base is the write model; the content-addressed index is the read model; projections are views materialized off the read model. A projection may be a website build, an essay rendering, a generated audio overview, an application scaffold, an image, a video. The projector may be a compiler, a template engine, or a model. The substrate stays domain-blind; all flavor comes from the knowledge base it serves.

The horizon this enables: a subject-matter expert matures their unique expertise into a knowledge base, and projections turn that one durable asset into whatever surface an audience needs — without the expert's knowledge ever leaving the asset they own. Licensing attaches to the knowledge base and its projections; the knowledge itself is licensed, never assigned.

## The Projection Contract — Three Settled Rules, Three Open Tensions

A projector that honors the model:

- **Reads only the read model.** No reaching around the index into raw substrate; no privileged side-channels.
- **Never mutates canon.** Projection is one-way. Insights produced during projection re-enter the knowledge base only through the write path — authored, reviewed, gated. (Per `models-do-not-mutate-canon`.)
- **Carries provenance.** Every projected artifact declares which knowledge base, at which content version, through which projector — the envelope-time-fields pattern generalized from responses to artifacts.

Open tensions this principle exposes without adjudicating: how much governance a projector fetches live versus snapshots at projection time; whether a projection may compose multiple knowledge bases and how provenance composes when it does; and what staleness budget different artifact classes tolerate. Programs adjudicate these per projection pipeline; the rulings are overlay, the tension is core.

## Failure Modes — Artifact-as-Asset, Tangled Bases, Backflow, Orphan Provenance

- **Artifact-as-asset** — investing in artifacts as if they were durable; the knowledge that produced them lives nowhere, and the artifact cannot be regenerated when it goes stale.
- **Tangled knowledge bases** — multiple concerns cohabiting one repository until no projection can tell whose governance it is projecting. (Observed: a personal overlay, a portable methodology, and a tool manual shared one repo for months; untangling took a governed bifurcation.)
- **Projection backflow** — a projector writing its outputs or opinions into the canon directly, collapsing the write/read split.
- **Orphan provenance** — artifacts that cannot name their knowledge base, version, or projector, making staleness undetectable and trust unearnable.

## Status and Evidence — One Lived Architecture, Two Corpora, Direction Not Yet Proof

Draft. Grounded in one program's lived architecture: a substrate (oddkit) serving two unrelated corpora through identical actions; a bifurcation that restored one-knowledge-base-per-concern; and existing canon this principle generalizes (artifacts-are-ephemeral, prompt-over-code, vodka architecture, D0002). The multi-expert horizon is stated as direction, not as established fact.

## Retraction Conditions — Beaten by an Artifact-First Workflow, or Broken by a Pipeline

- Retract or rescope if a mature program demonstrates that organizing around artifacts (with knowledge reconstructed on demand) outperforms organizing around the knowledge base for its class of work.
- The projection contract items harden into their own constraint once two independent projection pipelines validate them; if either pipeline shows a contract item unworkable, the item is amended here first.
