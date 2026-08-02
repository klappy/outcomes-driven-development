# The container boots, but it flies ungoverned
**Seed class:** candidate (observation → constraint proposal) — distilled by the scheduled distillation debrief, 2026-07-31 fire (sess_7c04c181).
**Claim:** The 2026-07-30 container-lane smoke PASS proves boot, shell/node, and GitHub egress — it does NOT prove a container flight can fly governed. Its own egress probe showed oddkit=520 and ars=401: a flight dispatched to that lane today cannot fetch canon, cannot check in, cannot heartbeat, and cannot debrief through ARS. That is precisely the silent-death class that killed the July 20–21 container cohort (runs fb133d81, 8bf49be4, 7efeae98, 9177ea77 et al., all lost/failed with no crewed debrief).

## Evidence (paid for in-window, 2026-07-30)
- run_347d8a4f debrief, verbatim: "VERDICT: PASS … EGRESS: github=200 oddkit=520 ars=401 … Proves container boots, shell/node work…" — log seq 17948–17950. The PASS is honest about its scope; the risk is a reader taking "PASS" as "lane ready."
- Casualty context: the pruned-run sweep in this same window re-surfaced the July 20–21 record — ~30 lost/failed container runs in two days (seq 17683–17693, 17883–17893 prune entries). Every one died registry-dark.

## Proposed constraint
No production flight is seeded to the container lane until a smoke run proves the full governance loop from inside the container: oddkit fetch 200, ARS checkin + heartbeat + debrief round-trip. "Boots" is a lane property; "governed" is the launch criterion. A lane smoke verdict should therefore be two-valued — BOOTS: PASS/FAIL and GOVERNED: PASS/FAIL — so a partial pass cannot masquerade as readiness.
