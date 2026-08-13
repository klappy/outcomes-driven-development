# Fly-Loop Annex — ODD Extraction Cycle (outcomes-driven-development)

**Status:** DRAFT — proposed annex under the ALREADY-RATIFIED stewardship charter (`canon/governance/stewardship-charter.md`, E0010, ratified 2026-06-09 by owner, in effect). Charter amendments are owner-reserved; this annex activates only on Klappy's ratification. It adds the loop's cadence, cost, and watch-list — it does not compete with, restate, or amend the charter's authority.
**Abbreviation:** **ODD** (outcomes-driven-development). A prior draft circulated as "OWD" — the W was a hallucinated letter, corrected by the captain 2026-07-06.
**Genre:** Editorial / curation (per the CDO rulebook's genre taxonomy) — falsifiable definition of *caught-up*: source watermark vs. processed watermark, over a source this loop does not own.
**Refines:** the CDO flight `research/stewardship-charters/owd-charter-draft.md` (2026-07-07), with cycle-01 observations replacing its estimates.
**Authored:** 2026-07-07, ODD Fly cycle 01 (Fable, verified `claude-fable-5`).

## Mission — what "caught-up" means

Healthy = **the bifurcation stays current and the split stays clean.**

- Every klappy.dev doc carrying `target_repo: "outcomes-driven-development"` in frontmatter is either present in this repo (byte-identical after dropping the `target_repo` line, or divergent only by a recorded criterion-6 genericization) or held on a recorded contested verdict.
- **Two parallel canons, both intact.** `klappy://canon` keeps its voice untouched — this loop never writes to klappy.dev, ever. URIs are grandfathered opaque keys: an extracted doc keeps its `klappy://` URI verbatim (observed convention across all 156 in-sync docs; D0002 "write-path re-shard").
- Neutrality holds where it applies: literal operational values genericized to placeholders (criterion 6 — worked example: `canon/methods/governance-validation-via-agents.md`, `klappy/klappy.dev` → `[OWNER]/[REPO]`); proof-of-provenance instance material kept (criterion 5).
- The read model serves every landed doc (oddkit catalog/get against this repo); the journal never gaps (ratified charter goal 5).

**Watermark at cycle 01 (observed 2026-07-07Z, klappy.dev @ 1a4919c):** 164 marked docs → 156 in sync, 5 missing, 2 stale, 1 divergent-by-design (the criterion-6 precedent). After this cycle's PR merges: 162 in sync, 0 missing, 0 stale, 1 contested held (`discernment-transfer-ladder`), 1 divergent-by-design.

## The extraction protocol (summary — full procedure in `extraction-workflow.md`)

1. **Board** under the ratified charter (fetch it; an unboarded session holds no authority).
2. **Watermark diff:** klappy.dev commits since last recorded sync, filtered to files carrying `target_repo: "outcomes-driven-development"` — parsed from frontmatter, never body-grepped (named failure mode: body-text routing).
3. **Screen** each candidate against the seven tests of `canon/constraints/core-boundary-criteria.md`. Verdict per doc, recorded with criterion numbers: route / stays-overlay / contested.
4. **Transform:** verbatim copy minus the `target_repo` line; URI unchanged; genericize only literal operational values (criterion 6), recording each placeholder.
5. **Land as a routing PR** carrying the evidence core-boundary-criteria §Verification demands: (a) frontmatter-parsed mover list, (b) before/after parity counts, (c) per contested doc, the criterion and one line of why, (d) canonical-copy declaration for anything genericized or split.
6. **Ratification gate: the captain's merge is the ratification.** Nothing reaches live serve (main / the read model) without it. Contested calls ride the decision board — tension exposed, never adjudicated by the steward.
7. **Verify + journal:** read-model check on landed docs, DOLCHEO trail in `journal/`, advance the watermark.

## What stays with the captain

The ratified charter's reservations, whole: the license (undeclared by decision — "licensed, never assigned"), repo settings/visibility/credentials, epoch declarations and charter amendments (including this annex), external contributors, the standing veto. Plus loop-specific:

- **klappy.dev is monitor-only.** Any fix this loop wishes the source would make is a note to the captain, never a PR to his canon.
- **Contested routings** — surfaced with the tension exposed.
- **Marking docs for routing.** The `target_repo` field is the maintainer's declaration; the loop reads it, never writes it. An unmarked doc, however portable it smells, is at most a decision-board suggestion.
- **Retiring or replacing an original: structurally out of scope**, not merely reserved. Additive, always.

## Cost cap

Normal cycle $2–4; per-run cap $5; a declared backlog-burn may run to $8 once, announced. Check-in: any cycle over $8, or two consecutive cycles where drafting outruns screening (spend shape inverting = curation drifting into authoring).

## Failure modes watched

| Signal | Threshold |
|---|---|
| The seven routing failures (topic-yanking, body-text routing, stranded derivation, manuals-as-philosophy, bets-as-doctrine, literal leakage, double-homing) | Any instance → journal incident |
| Watermark age | > 30 days behind klappy.dev → escalate, don't silently catch up |
| Voice/frame bleed in a landed doc | Caught at PR review; two in a row → recalibrate with the owner |
| Reverse bleed (any write, or proposed write, to klappy.dev) | Immediate stop — charter-surrender class |
| Read-model divergence (oddkit serves stale/missing marked docs) | Same cycle |
| Silent substitution (session operating without fetching the charter) | Has already resigned the charter (its own retraction clause) |
| **Authoring-home drift** (observed live, cycle 01): new core-routed docs born in klappy.dev while this repo's README claims authoring happens here | Re-report every cycle until the captain rules on the authoring home |

## Cadence

Weekly + event-driven: a klappy.dev merge touching marked docs; a read-model change affecting serving; an owner veto (calibration data). Cycle 01 was the backlog burn (5 missing + 2 stale, landed as one routing PR).

---
*Runs under the ratified E0010 charter's authority. Revocable with a word; revocation is journaled and the repo reverts to direct owner maintenance.*
