# First Distillation Sweep — 2026-07-20

**Status: DRAFTS LANDED, AWAITING VALIDATION PASS.** Start time: 2026-07-20
(per charter dispatch, C1). This report updates incrementally; each seed's
disposition and each promotion draft was committed and pushed as it landed —
see commit history on `sweep/2026-07-20-first-distillation` for the
incremental trail.

## Verdict

**VERDICT: SWEPT 3-promote/3-hold/1-fold** (of 7 seeds). Not every seed
promotes — an honest sweep, per the PRD's own anti-goals. All 3 promotions
are drafted, patch-verified against klappy.dev main, and delivered via the
fallback path (klappy.dev push refused, 403 — see §Push Attempt below).

## Per-seed disposition

| # | Seed | Disposition | Why (one line) |
|---|------|-------------|-----------------|
| 1 | policies-vs-requirements split | **PROMOTE** | Captain-ratified category split, canon-shaped, no existing canon doc covers it — drafting P#### against a new canon principle doc. |
| 2 | rebuild-vs-modify tipping point | **HOLD** | Philosophy already stable canon (`canon/principles/bulldoze-but-keep-the-blueprint.md`); the seed's own text admits the specific ask (a named threshold/metric, the one-layer-at-a-time rule) is undefined — nothing proposable to draft yet. |
| 3 | expectation retrospectives v0 rubric | **HOLD** | Explicitly a "first stab, to refine over time" (source frontmatter); one application to date (this very charter's §6). Pipeline evidence bar wants repeated validation before canonizing a rubric; premature to promote v0. |
| 4 | learning-to-learn meta-skill | **PROMOTE** | Best-evidenced seed — five distinct same-day receipts across two repos (casualty→law, validators failing authors twice, guards catching creators, cross-seat debrief-driven fix, captain's bridge/architecture catch); derives cleanly from the stable `trust-kernel` principle. |
| 5 | debrief: "a cache is a lie in wait" | **FOLD → seed 6** | Substance is already exhaustively covered by stable canon (`odd/constraint/anti-cache-lying.md`, E0005); the recurrence is not a new claim on its own — it is evidence *for* seed 6's claim (canon existing didn't prevent a second violation because nobody searched it at design time). Folded in as evidence, not drafted standalone. |
| 6 | debrief: "search canon before designing" | **PROMOTE** | Names a real operational gap in existing canon (`canon/constraints/mode-discipline-and-bottleneck-respect.md` currently says "search canon before asking," not "before designing") with a concrete, low-risk proposed addition. Evidence is a single occurrence — flagged honestly in the promotion's own Evidence section for the maintainer to weigh (defer/accept/reject are all legitimate outcomes here). |
| 7 | debrief: "dual-context vocabulary" | **HOLD** | Single application (memento-for-machines essay); substantively overlaps the charter's own C4 item (klappy.dev PRs #303/#304, "voice & attribution," explicitly gated behind C1 and scoped to *propose, don't self-canonize*). Drafting a promotion here would preempt C4's lane. Held and flagged for the C4 owner. |

## Promotions drafted

All three land in this repo (`docs/promotions/`) as a promotion doc + a
git-apply-able `.patch` per promotion — checked (`git apply --check`) clean
against `klappy/klappy.dev` main.

| ID | Title | Target canon doc | Risk | Evidence honestly flagged |
|----|-------|-------------------|------|----------------------------|
| P0011 | Policies vs. Requirements — split an overloaded category | `canon/meta/policies-vs-requirements.md` (new) | Low | Evidence class is a direct captain ratification, not repeated-validator-failure — named as a different evidence class than this pipeline's usual bar. |
| P0012 | Learning to Learn Is the Meta-Skill — triple-loop debrief review | `canon/methods/triple-loop-debrief-review.md` (new) | Low | 5 distinct same-day receipts, 2 repos, 0 cross-session recurrence yet — weaker independence than e.g. P0002's 6 cross-repo occurrences over months. |
| P0013 | Search Canon Before Designing, Not Just Before Asking | `canon/constraints/mode-discipline-and-bottleneck-respect.md` (append) | Low | 2 design decisions, same incident — below the pipeline's usual ≥2-*independent*-incidents bar; promotion explicitly recommends `deferred pending a second, separate incident` is a legitimate maintainer outcome. Seed 5 ("a cache is a lie in wait") folded in here as supporting evidence, not independently drafted, since its substance duplicates already-stable canon (`odd/constraint/anti-cache-lying.md`, E0005). |

## Push Attempt / Fallback

Attempted a probe push of a throwaway branch to `klappy/klappy.dev` before
drafting, per the charter's PR-mechanics instruction. Result: **refused**
(`remote: Permission to klappy/klappy.dev.git denied to git-repo-auth[bot]`,
HTTP 403). This is the documented, expected fallback trigger, not a failure:
each promotion doc + patch is committed on this repo's sweep branch instead.
Probe branch was never pushed and was deleted locally; no trace left on
klappy.dev.

## Branches pushed / PRs owed

- **Pushed:** `sweep/2026-07-20-first-distillation` (this repo,
  `klappy/outcomes-driven-development`) — carries this report, the foldout
  TSV, and all three promotion docs + patches, committed incrementally.
- **PRs owed to the dispatch seat** (klappy.dev push access required):
  1. `docs/promotions/P0011-policies-vs-requirements-split.md` +
     `.patch` → apply against `klappy/klappy.dev` main, open PR.
  2. `docs/promotions/P0012-learning-to-learn-triple-loop-review.md` +
     `.patch` → apply against `klappy/klappy.dev` main, open PR.
  3. `docs/promotions/P0013-search-canon-before-designing.md` + `.patch`
     → apply against `klappy/klappy.dev` main, open PR.
  All three patches verified clean (`git apply --check`) against
  `klappy/klappy.dev` main as of this sweep's run. Apply with
  `git apply <patch>` from a klappy.dev checkout, then commit + push a
  branch + open PR; the promotion doc's own frontmatter/body is the PR
  description material.
- No PR owed against `klappy/outcomes-driven-development` itself — this
  sweep's own artifacts (report, TSV) merge via this repo's normal PR flow
  if the maintainer chooses; C1's charter does not require merging the
  sweep branch itself, only landing the drafts in a terminal, durable state.

## Validation verdict

(pending — spawning fresh subagent next)
