# PRD — The Second-Brain Feeding Loop: Canon Grows From Lived Flight Experience

**Status:** DRAFT — captain review required; nothing here is policy until merged.
**Mode:** planning — required output: PRD (`klappy://ars/policy/mode-output-contract`).
**Flight:** fl-95bffe0b · 2026-07-14 (captain civil date, America/New_York; flight clock observed 2026-07-15T02:36Z UTC via `oddkit_time`).

> 🎯 **One line:** every flight already records what it lived; nothing distills those
> records into canon. This PRD adds the missing loop — one debrief line per lesson at
> the source, one batched fold flight that drafts canon PRs, captain merge as the only
> promotion — so the second brain grows from experience, not from document dumps.

---

## 1. Problem — recorded is not remembered

Captain standing direction (2026-07-14 ET): everything everyone does should
**constantly feed the company's second brain out of lived experience** — not by
pumping it full of historical documents. The corpus grows from what flights learn
while flying, distilled into canon.

Today the system records superbly and distills almost never.

## 2. Exploration inventory — what exists, cited live

| Mechanism | Captures today | Feeds canon? |
|---|---|---|
| `oddkit_encode` + DOLCHEOT (`klappy://canon/definitions/dolcheo-vocabulary`) | Structures D/O/L/C/H/E/O/T artifacts at natural breakpoints; **does not persist** — caller must save (`klappy://docs/oddkit/proactive/encode-does-not-persist`) | No |
| Recorder duty (`klappy://ars/policy/dispatch-brief-conventions` v0.7.0 §RECORD) | One journal entry per flight, CDO `journal/`; dual-write per k0203 | No |
| Kirigami foldouts (same policy §convention 3, v0.5.0) | Captain decisions — one twelve-column TSV row each (ruling + reasoning + axiom + rejected) | No |
| Lithos streams (same policy v0.6.0a) | ALL run outputs, appended at every checkpoint; repo is the cold store | No |
| fold / recall / unfold / archive (kirigami MCP) | Stateless foldout ingestion, retrieval, expansion, archival | No |
| Promotion Pipeline (`klappy://docs/promotions`) | The **only** recorded→canon path; a human-authored promotion artifact per proposal | Yes — manual, ad hoc |

**The gap, named precisely:** records accumulate at near-zero marginal cost, but
distillation — observations becoming principles and constraints someone actually
fetches — is ad hoc, manual, or missing. `klappy://docs/oddkit/encode-persistence-gap`
already legislated the adoption half ("if the agent has to be prompted, the system has
failed"); this PRD closes the distillation half. The Promotion Pipeline is the right
destination; it lacks a feeder.

## 3. The loop — policy + minimal mechanism

### (a) At the source: the CANDIDATES debrief duty (near-zero marginal cost)

Amend `klappy://ars/policy/dispatch-brief-conventions` (→ v0.8.0): every flight
debrief names its canon-candidate lessons explicitly, one line each:

```
candidate: <observation|principle|constraint> — <one line>
```

A flight with nothing to promote writes `candidates: none` — an honest zero, not a
skipped duty. Cost per flight: one line per candidate in a debrief the flight already
writes (or the single honest-zero line).

### (b) The batch: a periodic distillation fold flight

A fold flight runs on a cadence (decision card 1), reads **deltas since its last
watermark** — new CDO journal entries, kirigami foldouts, Lithos stream checkpoints,
and CANDIDATES lines — clusters recurring lessons, and **drafts canon PRs** through
the existing Promotion Pipeline. Observations first; a candidate is drafted as a
principle or constraint only when repeated evidence across flights supports it.
Nothing is promoted by the fold flight itself: **the captain's merge is the only
promotion.** The fold flight commits its watermark so no record is read twice.

### (c) Anti-goals — stated as law

1. **No bulk document dumps.** Historical archives are not canon feed; the loop reads flight records, not file shares.
2. **No auto-promotion.** Drafted canon lands as a PR assigned to the captain; unmerged drafts expire, they do not accumulate authority.
3. **No duplicate-of-journal canon.** A drafted canon doc must distill across records and carry a claim the journal alone does not; otherwise the right artifact is a pointer, not a page.

### (d) Measurement

Weekly: (i) canon docs merged with flight-sourced-candidate provenance vs
manually authored; (ii) CANDIDATES lines emitted per flight (including honest
zeros); (iii) candidate→merged conversion rate. The loop is working when
flight-sourced canon growth is nonzero weekly with no captain effort beyond merges.

## 4. Tower-load budget (captain's explicit caveat)

Per flight: one debrief line per candidate (or the single honest-zero line). Captain:
merge review of batched canon PRs only. Heavy lift: entirely inside the batched fold
flight. No new per-flight ceremony.

## 5. Decision cards (first OPT = recommendation)

1. **Cadence** — OPT: weekly, riding the existing tower sweep — no new schedule surface; OPT: dedicated scheduled fold flight — tunable cadence, one more moving part; OPT: threshold-triggered at N queued candidates — responsive but bursty.
2. **Who drafts** — OPT: the tower-sweep seat gains a distillation pass — reuses an existing duty; OPT: a dedicated fold-flight class with its own brief — cleaner mode discipline, more dispatch overhead.
3. **Where candidates queue** — OPT: harvested from debrief/journal text by the fold flight — zero new infrastructure; OPT: a `canon-candidates` board workstream, one item per candidate — visible but noisy; OPT: an append-only `candidates.foldout.tsv` in this repo — kirigami-native, one more file to tend.

## 6. Rollout

1. Captain merges this PRD (ratifies the direction).
2. Dispatch-brief-conventions v0.8.0 amendment adds the CANDIDATES duty.
3. First fold flight runs bounded backfill-lite (last N journal entries only — a watermark seed, not a bulk dump).
4. Two weeks of measurement → debrief → the debrief legislates adjustments.

## 7. Non-goals

Bulk-archiving historical documents; auto-writing canon; replacing the Promotion
Pipeline (the fold flight **feeds** it, never bypasses it).

---

*This flight practices what it preaches — its own debrief carries CANDIDATES lines.*
