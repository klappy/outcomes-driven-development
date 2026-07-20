---
status: candidate
date: 2026-07-20
source: "captain, in-session framing to the Otto seat, 2026-07-20 (triple-loop retrieval-on-time thesis)"
attribution: "Klappy (thesis); evidence from Move 4 D-OR2 mishap + this morning's captain framing"
derives_from: "klappy://canon/values/trust-kernel — expectations are only kept if the relevant constraint is actually consulted at the moment it bears"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md) — awaiting distillation sweep; promotion is the captain's merge alone"
---

# Decision-Surface Trigger Map — Bind Canon Lookups to Decision Verbs

**Thesis (captain, verbatim intent, 2026-07-20):** retrieval-on-time is the
frontier, not recording. Canon can exist, be findable, and still not fire —
the gap is not that the ruling was missing, it's that the planning moment
never looked it up.

## The pattern

D-OR2 (subscription-auth lane) existed and was findable in canon the entire
time Move 4 was being scoped. `oddkit_challenge` — the standing mechanism for
surfacing a counter-consideration before a plan locks — existed all session
and was never fired at the Move 4 planning moment. The miss was not a
recording failure; the record was there. It was a retrieval failure: nothing
bound the act of scoping a deletion to the act of searching for the ruling
that could contradict it.

## The proposal

Bind mandatory canon lookups to decision **verbs**, not to topics or
vibes-based judgment calls about whether a search "seems warranted":

- `delete` (a lane, a subscription path, a stored capability) → search
  rulings that **created** the target before scoping its removal.
- `design` (new architecture, new mechanism) → search P0013 and the
  design-time canon-search corollary already ratified 2026-07-19
  (`candidates/2026-07-19-learning-to-learn-meta-skill.md` neighbor seed:
  "search canon before designing").
- `spend` (economic commitment, tier choice, vendor lane) → search
  auth/economics rulings before the commitment is scoped, not after.

Mechanism over promise: a preflight check can **refuse** a deletion charter
that cites no searched rulings for the target it proposes to delete. This is
enforceable the way a lint rule is enforceable — it doesn't depend on the
seat remembering to be careful.

## Evidence

Single-incident-class evidence, from two related angles in one shift:

- Move 4 as scoped deleted the D-OR2 subscription-auth lane; the captain's
  hold (recorded PR #106 comment + PRD foldout) caught it, not a mechanism.
- The category error underneath: lanes were labeled on the technical axis
  (which code moves where) when the load-bearing axis was economic (D-OR6 vs
  D-OR2 cost/subscription tradeoff) — the two were never reconciled because
  nothing forced the reconciliation to happen at scoping time.

## Open question for ratification

Whether the preflight refusal is enforced by a gate (hard block) or a
warning (soft nudge) is not resolved here — this seed names the trigger-verb
binding and the mechanism-over-promise principle; it does not specify the
enforcement tier.
