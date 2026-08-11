# A schedule is a declared expectation — audit its fire times, don't assume them

**Seed class:** candidate observation — distilled by the twenty-first scheduled distillation fire (sess_2aaf07b3), 2026-08-10 (captain civil date; fired 2026-08-11T01:01Z UTC).

**Claim:** A scheduled charter's cadence is itself an expectation set with the captain, and it drifts silently. The tower-sweep charter, expected in the morning lane (observed firing 09:34Z on 08-09), fired instead at 21:33Z on 08-10 (sess_76d97591, log seq 33123) — and no morning firing appeared in the log at all that day. The sweep itself flagged the same evening-firing pattern on 08-08b. The work landed cleanly both times, so no per-flight expectation broke — which is exactly why cadence drift is invisible to the per-flight expectation audit: every individual flight scores "set and kept" while the schedule quietly stops being the schedule the captain set. The clock rule already says observe time, never infer it; this extends it to the calendar of the fleet: fire times are observable in the log (seat-boarded timestamps) and must be compared against the declared cadence as part of the audit, not assumed from the schedule's intent.

## Evidence
- seq 33123 (2026-08-10T21:33:40Z): seat-boarded sess_76d97591, tool cowork-tower-sweep — evening firing; no morning sweep entry in the window (seq 33121–33124 is the complete window).
- claude/sweep-registry-hygiene-2026-08-10.md: "this run fired ~17:33 EDT — the duplicate-evening-firing pattern flagged 08-08b recurred; the 09:34Z morning firing did not appear today."
- claude/sweep-registry-hygiene-2026-08-09.md precedent: morning-lane firing at 09:34Z.
- Both firings delivered CLEAN SWEEP debriefs — per-flight audit alone would never surface the drift.

## Proposed canon shape
Observation: the expectation audit has a fleet-cadence layer above the per-flight layer. Each scheduled charter carries a declared fire window; the periodic audit (distillation or sweep) compares observed seat-boarded timestamps against it and files drift as a broken expectation of the schedule, even when every flight inside it landed clean. Silent cadence drift is the schedule's version of a silent death.
