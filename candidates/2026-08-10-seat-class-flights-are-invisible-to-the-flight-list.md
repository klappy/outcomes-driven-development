# Seat-class scheduled charters are invisible to ars_flight_list — window audits must read the log

**Seed class:** candidate constraint — distilled by the twentieth scheduled distillation fire (sess_b513eb72), 2026-08-09 window (fired 2026-08-10T01:04Z).

**Claim:** This fire pulled the full durable flight registry (ars_flight_list, 444 rows, untruncated) and found the newest heartbeat at 2026-08-08T01:02:39Z — a registry that appears silent for the entire audit window. It was not silent: the 08-09 tower sweep (sess_c99d6861) boarded and landed at 09:34–09:35Z, plainly visible in the coordination log (seq 33118–33119). The sweep boarded seat-class (as every scheduled charter has since the 07-27 "pin the checkin class" seed), and ars_flight_list excludes seats unless include_seats:true is passed. A distillation that audited the window from the flight list alone would have scored a kept expectation as a silent death — the worst class — and been wrong. The registry's flight surface and the log disagree by design; the log is truth.

## Evidence
- ars_flight_list full snapshot this fire (tool-result file …/mcp-ARS-ars_flight_list-1786323897799.txt): count 444, truncated false, max last_heartbeat_at 2026-08-08T01:02:39Z.
- ars_log_read seq 33118 (seat-boarded sess_c99d6861, 2026-08-09T09:34:21Z) and 33119 (flight-landed, 09:35:23Z) — inside the window the flight list shows as empty.
- Corroborating durable doc: claude/sweep-registry-hygiene-2026-08-09.md (CLEAN SWEEP).
- Prior seed lineage: PR #34 (2026-07-27, "scheduled charters must pin the checkin class") created the seat-class population this blind spot hides.

## Proposed canon shape
Constraint (distillation/sweep charter conventions): any window audit over registry state MUST use ars_log_read (log as truth) or ars_flight_list with include_seats:true; registry-silence conclusions drawn from the default flight surface are inadmissible. Corollary: when one seed changes a population's class (PR #34), the surfaces that filter by class inherit a blind spot — audit the read paths after changing the write path.
