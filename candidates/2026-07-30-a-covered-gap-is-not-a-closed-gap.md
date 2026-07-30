# A covered gap is not a closed gap (recovery without diagnosis)

**Seed class:** candidate observation — drafted by the scheduled distillation seat (third loop), 2026-07-29 window.
**Claim:** When a scheduled loop returns after a dark day, covering the missed window is necessary but not sufficient. The tower-sweep loop came back on 2026-07-29 and did the right half: it named the miss ("no sweep fired 07-28") and widened its window to cover 07-27T21:35Z → now, so no registry state went unaudited. But the *cause* of the miss was never established — not by the returning sweep, not by any other loop, not by a malfunction entry. A failure whose cause is unrecorded is a failure the fleet is scheduled to repeat.

## Evidence (paid for in the window)

- Recovery observed: sweep sess_3944aa76 boarded 2026-07-29T12:01:18Z (log seq 17539), landed clean 12:02:44Z (seq 17540–17541) with a crewed debrief and doc `claude/sweep-registry-hygiene-2026-07-29.md`. The doc explicitly names the gap and states the widened window — the gap-covering half worked and is worth encoding as the norm.
- Diagnosis absent: nothing in the sweep doc, the debrief, the log, or the registry says *why* 07-28 fired zero sweeps. The schedule presumably still exists (07-29 fired on time at the usual 12:01Z slot); the miss self-healed without anyone learning what broke.
- Prior art: yesterday's seed (PR #36) covers *detection* of the dark day. This seed covers the day after: detection happened, recovery happened, diagnosis never did. Expectation audit score for the window's one flight: expectation set and kept (the sweep) — but the standing meta-expectation "failures get causes" was broken silently.

## Why it matters

The debrief loop's premise is that failures become canon so they don't repeat. A schedule miss that ends in silent recovery skips the debrief entirely: there is no flight to debrief (never born) and the returning flight treats the gap as scenery, not as its own casualty to investigate. The failure class from PR #36 — invisible misses — compounds into a second class: undiagnosed misses that look resolved because traffic resumed.

## Suggested landing

Principle (debrief discipline, second-brain-feeding-loop adjacent): a returning scheduled loop owns the gap it returns across — its first landing after a miss must either state the cause of the miss or explicitly record "cause unknown, needs captain/tooling" as an open item, never merely note the gap and move on. Cheap mechanical variant: the sweep/distillation templates get one line — "if your watermark shows a missed fire, the miss's cause is part of this run's deliverable."
