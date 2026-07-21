# Debrief — Overnight/Morning Shift (2026-07-19 evening → 2026-07-20)

**Charter:** `odd/charters/2026-07-20-successor-charter.md` (activated on the
maintainer's word).
**Governing PRD:** `docs/prd/2026-07-14-second-brain-feeding-loop.md`
(second-brain feeding loop — the loop this shift closed end-to-end for the
first time).
**Method applied:** `klappy://canon/methods/triple-loop-debrief-review`
(klappy.dev, landed as active canon **this morning**, 2026-07-20 —
this debrief is its first canonical application).

> Archival register: substance and lesson, not narration. Facts below are
> session receipts.

---

## SHIPPED (with receipts)

- Successor charter activated; auth & provider strategy PRD authored
  in-seat at Fable 5 (captain model-tier ruling), validated fresh
  (`run_44cd2483` PASS), merged `1f31d6c` (agent-role-service #111). Forks
  1/4/5/6 ratified; §3 amended to two-tier per captain's OpenRouter steer;
  §2 open pending §3.
- Captain ruling: **hold Move 4** — as scoped it deleted the D-OR2
  subscription-auth lane (recorded on PR #106 comment + PRD foldout).
- First distillation sweep **TERMINAL**: 3-promote / 3-hold / 1-fold
  (`run_fb133d81`, branch `sweep/2026-07-20-first-distillation`). P0011 and
  P0012 promoted, captain-merged, **LANDED AS ACTIVE CANON same morning**
  (klappy.dev `3703ad8`, `ce20887`). P0013 pending. The loop closed
  end-to-end for the first time in one shift: flight → seed → sweep →
  promotion → ruling → canon.

## MISSES (single loop → what was fixed)

- Four ceiling/infra casualties on agent-role-service **write** flights:
  `run_7efeae98` (lost), `run_8bf49be4` (timeout, 600000ms),
  `run_dcb7c73b` (lost **unpushed** — violated its own push order),
  `run_3bdf1c70` (http 502), `run_af7164c6` (lost). Read-only and ODD
  flights were unaffected all shift. Diagnostic flight `run_1e840fcf`
  chartered to isolate the write-path failure class.
- The seat deleted a PR branch before observing the merge receipt,
  auto-closing the captain's PR #306; recovered in seconds. Law adopted:
  destructive cleanup never shares a command block with the action it
  follows — it waits for the observed receipt, not an assumed one.
- Narration drift: "tonight" used after dawn despite `oddkit_time` being
  observed every turn — observation without application. Law adopted:
  day-part language derives from currently observed civil time, not from
  when the session started.

## DOUBLE LOOP — what law changed as a result

- **Slice law ratified** (PRD §5): push-early made loss #3
  (`run_dcb7c73b`) recoverable where losses #1/#2 lost everything outright.
  Loss `run_dcb7c73b` itself confirms the corollary: unpushed work is the
  only kind that dies. This debrief was drafted under that same law —
  branch pushed and each section committed as it landed, per the
  push-first instruction governing this shift's close.
- **Tier law** (captain ruling): strategy-class planning is Fable-tier. The
  Move 4 mishap was a category error, not a technical mistake — lanes were
  labeled on the technical axis (which code moves where) when the
  load-bearing axis was economic (D-OR6 vs D-OR2 cost/subscription
  tradeoff), and the two axes were never reconciled at scoping time.

## TRIPLE LOOP — did the learning machinery itself perform?

Applying `triple-loop-debrief-review`'s standing question for the first
time since it landed as canon this morning:

- **Retrieval-on-time is the frontier, not recording** (captain framing,
  this morning). D-OR2 existed in canon and was findable the whole time
  Move 4 was scoped; the miss was not that the ruling was absent, it's that
  the planning moment never fired the lookup. `oddkit_challenge` existed
  all session and was never invoked at the Move 4 decision point. The
  learning machinery recorded correctly and retrieved too late — the
  captain's catch substituted for a mechanism that doesn't yet exist. Seed
  filed: `candidates/2026-07-20-decision-surface-trigger-map.md`.
- **Unknown-unknowns: surprise is the trigger, the crew is the coverage.**
  Four blind-spot catches landed in one shift, from four non-overlapping
  vantages — the captain caught both the time-drift and the auth-economics
  category error, the validator caught evidence-framing overreach in a
  promotion draft, the plan flight caught stale line counts, and the seat
  itself caught the D-OR2-vs-Move-4 conflict. No single vantage caught more
  than two; diversity of reviewing role, not depth of any one review, is
  what closed the coverage. Seed filed:
  `candidates/2026-07-20-surprise-is-the-trigger-crew-is-the-coverage.md`.
- **Verdict on the machinery this shift:** the record-and-distill half of
  the loop worked completely for the first time (flight → seed → sweep →
  promotion → ruling → canon, same morning). The retrieval-at-decision-time
  half did not yet have a mechanism — it had the captain's attention, which
  is not a substitute the loop can rely on at scale. That gap is this
  shift's clearest triple-loop finding, and it is the reason the two
  trigger/coverage seeds above are framed as mechanisms ("preflight can
  refuse...") rather than as further reminders to be careful.

## CANDIDATE SEEDS filed this shift

Filed to `candidates/`, each its own file, honest evidence sections
(single-incident evidence flagged as such where applicable):

1. `2026-07-20-decision-surface-trigger-map.md` — bind mandatory canon
   lookups to decision verbs (delete → search rulings that created the
   target; design → P0013; spend → auth/economics rulings); mechanism over
   promise — preflight can refuse deletion charters that cite no searched
   rulings. Evidence: Move 4 + this morning's captain framing.
2. `2026-07-20-surprise-is-the-trigger-crew-is-the-coverage.md` —
   unknown-unknowns are caught by expectation-deviation plus non-overlapping
   vantages, not foresight. Evidence: 4 catches, 1 shift.
3. `2026-07-20-destructive-cleanup-awaits-observed-receipt.md` —
   destructive cleanup waits for the observed receipt, never batched with
   the action it follows. Evidence: PR #306 incident (single incident,
   flagged as such in the seed).
4. `2026-07-20-day-part-from-clock-not-context.md` — day-part language
   derives from the observed clock, not session-start context. Evidence:
   single incident (flagged as such in the seed).

All four queue against the second-brain feeding loop
(`docs/prd/2026-07-14-second-brain-feeding-loop.md`); promotion is the
captain's merge alone, via the next distillation sweep.

## CLOSE-OUT DUTIES

### C3 — code tray dispositions (durable record)

| PR | Disposition |
|---|---|
| #80 | Ready-not-draft, spec-less. Needs a captain call or a spec before it can move — parked, not actioned, pending either. |
| #79 | Spec-less draft. Parked to the captain's board. |
| #83 | Spec-less draft. Parked to the captain's board. |
| #91 | Spec-less draft. Parked to the captain's board — but a spec is **derivable** from the durable-flight-registry policy already on file; the next seat that picks this up should draft that spec from the registry policy rather than re-deriving it from scratch. |

Note: a seat board write attempted this shift was correctly guard-denied
(2026-07-20) — board writes remain seat-guard-denied by design per the
charter's grants section; no exception was taken.

### Expectation retro (per charter §6 rubric)

| META-EXPECTATION (charter §6) | Met? | Note |
|---|---|---|
| **Feel** — calm and boring, casualties rare and instructive | Mostly | The write-path casualty cluster (5 lost/timeout/502 flights) was thematic, not rare, on one lane; read-only and ODD flights stayed calm all shift. Diagnostic flight chartered rather than absorbed as noise. |
| **Bounded** — success within a sitting, M-tray cleared in budget | No | The write-path ceiling casualties exceeded "rare and instructive" — this is the shift's clearest unmet expectation, not a rounding error. |
| **Validated** — every landing G5'd | Yes | Sweep (`run_fb133d81`), PRD merge (`run_44cd2483`), and the promoted canon docs all carry fresh validation receipts. |
| **Durable** — no outputs-only artifacts | Yes, after the slice law | Loss `run_dcb7c73b` was unpushed and died; every other landing this shift is a repo commit or a merged SHA, not a session-local file. The slice law (push-early, push-per-section) is why this debrief itself is being drafted the same way. |

### Open items carried forward

- P0013 (pending, from the first distillation sweep — not yet promoted).
- ODD-publicity-audit (not run this shift).
- Forks 2/3 of the auth & provider strategy PRD (not yet ratified; §2
  remains open pending §3).
- M2 — Actions tab glance (CI execution visibility; seat tokens cannot
  hold `actions:read`, needs a maintainer glance).
- Diagnostic flight `run_1e840fcf` — write-path casualty root cause, result
  not yet in hand as of this debrief's close.

---

*The black box records; the debrief legislates; the crew flies again.*
