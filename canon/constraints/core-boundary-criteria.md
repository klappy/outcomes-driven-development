---
uri: odd://canon/constraints/core-boundary-criteria
kind: canon
title: "Core Boundary Criteria — What Belongs in the Portable Core, What Belongs Elsewhere"
audience: canon
exposure: nav
tier: 1
voice: neutral
stability: semi_stable
tags: ["constraint", "boundary", "routing", "core", "overlay", "tool-repo", "bifurcation", "smell-tests", "portability"]
relevance: decision
execution_posture: governing
date: 2026-06-09
derives_from: "odd/decisions/D0002 (canon storage model), canon/principles/scoped-truth.md, canon/principles/vodka-architecture.md"
complements: "canon/constraints/canon-integration-audit.md, canon/methods/governance-validation-via-agents.md"
governs: "Routing of documents across a federated knowledge base: the portable core, personal/instance overlays, and tool repositories. The criteria, the smell tests, the failure modes, and the evidence a routing decision must carry."
---

# Core Boundary Criteria — What Belongs in the Portable Core, What Belongs Elsewhere

> Three homes, one test each. The portable core holds what any adopter needs: principles, constraints, and methods whose substance survives leaving their birthplace. An overlay holds the maintainer's adjudications: chosen styles, identity, relationships, house genres, and frameworks still under personal validation. A tool repository holds that tool's user manual and maintenance manual — nothing else. The instance appearing as *proof* inside a core document is healthy provenance; the instance appearing as the *subject* is a routing error.

## Description

A federated knowledge base shards into a portable core, one or more overlays, and tool repositories. Every document has exactly one home, declared by physical membership and authority — never inferred from topic, path, or vocabulary. This constraint defines how to decide that home, how to smell a misrouted document, and what evidence a routing decision must carry. It was extracted from a live bifurcation in which every criterion below was minted by a maintainer correction to an over- or under-eager routing call.

## The Criteria

1. **Topic is not the routing criterion.** A document routes on whether *its substance* is portable, not on what domain it mentions. A principle about voice can be universal; a principle about caching can be parochial. Yanking documents by category ("it talks about writing") is the failure, not the discipline.

2. **Provisional found-frameworks stay in the overlay.** A framework the maintainer found and is still validating — "applied as working practice, retired when disconfirmed" — does not ship to adopters as core canon until proven. The overlay is where bets live; the core is where settled doctrine lives.

3. **An exposed tension is core; the ruling on it is overlay.** When a document names a tension — "it could be this or this, with a range between" — and does not adjudicate where on the range to land, that exposure is universal. The adjudication is the instance-specific part. Per-document test: does it surface what you must think through, or does it decide for you?

4. **Tool repositories are manuals only.** If a document is not about creating, maintaining, or using that tool specifically, it does not belong in the tool's repository. Principles a tool *embodies* are core; the tool being the proof does not make the principle tool documentation.

5. **Proof is not subject.** Instance-specific material inside a core document is healthy when it serves as evidence, worked example, or provenance ("the same ten actions serve a software canon and a theology corpus"). It is a routing error when the instance is what the document is *about*, or when the document cannot function without instance context.

6. **Operational values do not travel literally.** Hardcoded instance values — repository names, server URLs, account-specific commands, copy-pasteable prompts naming the maintainer's resources — must be genericized to placeholders in the core copy. An adopter copy-pasting core content must land in their own world, not the maintainer's.

7. **Documents travel with their derivation chains.** A document whose `derives_from` ancestry lives in the core belongs in the core, absent a stronger criterion. Stranding a document from everything it derives from is a smell that the routing followed topic, not substance.

## Smell Tests

Run these against a candidate corpus; score prose only — identity URIs are frozen opaque keys and are exempt:

- Maintainer or instance names in prose (not in URIs, not in code blocks)
- Named third parties and personal relationships
- Domain anecdotes that function as subject rather than as evidence
- Instance operations vocabulary (the instance's site sections, pipelines, publication mechanics)
- First-person voice in frontmatter (`voice: first_person`) — a soft smell: content may be portable while the telling is not; queue for re-voice on next edit rather than blocking
- Hardcoded operational values (URLs, repo slugs, account identifiers) outside clearly-marked examples

A high score is a trigger to read, not a verdict. Every signal above has a legitimate core use as proof (criterion 5).

## Failure Modes

- **Topic-based yanking** — removing portable principles because their examples wear instance clothing. (Observed: voice and architecture principles nearly pulled for mentioning writing and the tool.)
- **Body-text routing** — selecting movers by string-matching routing markers in document bodies; documents that *quote* the marker travel by accident. Routing fields must be parsed from frontmatter only. (Observed: the bifurcation DR shipped itself to two repos by quoting the enum.)
- **Stranded derivation** — moving a document away from its `derives_from` ancestry, or leaving one member of a principle cluster behind.
- **Manuals as philosophy** — setup and connect instructions shipped as core methodology. (Observed: an MCP getting-started doc in core.)
- **Bets shipped as doctrine** — provisional frameworks reaching adopters before validation completes.
- **Literal operational leakage** — adopters copy-pasting the maintainer's repo names and URLs from core templates.
- **Double-homing** — the same document maintained in two repos without a declared canonical copy; redundant state invites drift.

## Verification

A routing decision or audit PR must carry: (a) the parsed-frontmatter mover list (never a body-grep), (b) read-model parity or delta counts before/after, (c) for each contested document, the criterion number that decided it and one line of why, and (d) for any genericized or split document, which copy is canonical. Disagreement between an audit result and this constraint is itself a finding: fix the document, the organization, or this constraint — and record which.

## Defaults

- When no criterion clearly decides, the document stays in the overlay; the core must be pulled toward quality, not pushed toward volume.
- Re-voice, genericize, and split lazily — on next edit — unless the document is live-read by a tool, in which case coordinate the split with the tool's read path first.
- The maintainer's rulings are the calibration data; encode each correction as a worked example under the criterion it refined.

## Status and Evidence

Working canon, semi-stable. Every criterion was minted from a live maintainer correction during a single program's bifurcation (2026-06-09, ~230 routed documents): each failure mode listed above was observed, not hypothesized, and each is paired with the correction that fixed it. The sample is one federation; the criteria are treated as the working rule for the class of overlay/core/tool-repo splits, revisable on contact with a second federation.

## Retraction Conditions

- A criterion retires if applying it produces a documented misrouting in a second, independent federation — the fix then goes here, not in the routed corpus.
- Criteria 1 and 5 retire together if a counter-example shows substance and subject cannot be distinguished operationally for some document class.
- If an audit and this constraint disagree and the audit is judged right twice consecutively, this constraint is the bug.
