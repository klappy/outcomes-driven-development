# Theory of Constraints as the third loop (learning-to-learn)
**Seed class:** candidate — captain steering 2026-07-21, recorded by the dispatch seat.
**Claim:** Loop 1 does the work; Loop 2 (debrief/feeding loop) turns surprises into lessons; Loop 3 must rank effort and lessons by relevance to the CURRENT binding constraint on progress toward the Goal — and sunset lessons whose constraint has moved. Without Loop 3, Loop 2 optimizes local maxima with excellent discipline.

## Case study (2026-07-21, observed)
Overnight PR sweep: 03:13–07:52Z, ~4.5h, ~10 captain interruptions, 9 merges — ~1 merge per captain touch. The seat invested heavily in runtime-reaper workarounds (micro-charter law, recovery protocol, two PRDs) — real artifacts, but the reaper only binds flights >2min, which most work is not. Morning turn: ~18 min, 0 interruptions, 9 merges + full CI audit. Same lane, same reaper. The binding constraint was seat turn-cadence (captain used as scheduler), not the runtime. Improvement at a non-constraint is inventory, not throughput.

## Mechanism (proposed for debrief/tower-sweep template)
1. **Goal metric, named per cycle:** validated Goal-work landed per captain-minute consumed (first-revenue and transition milestones weight what counts as Goal-work).
2. **Constraint identification, with evidence:** each debrief names the current binding constraint and the observation that convicts it.
3. **Effort audit:** classify the cycle's effort and new lessons as constraint-relevant vs local-optimum. Local work may continue at best-practice quality, but elevation effort goes to the constraint.
4. **Step-five sunset review:** every standing lesson/law carries the constraint that birthed it; when that constraint moves, the law is re-validated or retired. Immediate example: micro-charter law P1 caps task size — MUST sunset when run-completion durability (ARS PRD #112) ships, or it becomes the next constraint. Its retraction condition is already written; the third loop is what makes checking it someone's job.
5. **Re-identify every cycle.** Yesterday's bottleneck fix is tomorrow's bottleneck.

## Known next-constraint candidates (to test, not assume)
Captain decision latency (fork queue depth/age); container-lane ceiling (binds only >2min jobs until #112 ships); seat context saturation per session.
