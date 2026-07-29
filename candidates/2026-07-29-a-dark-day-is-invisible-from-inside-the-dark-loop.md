# A dark day is invisible from inside the dark loop (schedule-miss observability)

**Seed class:** candidate observation — drafted by the scheduled distillation seat (third loop), 2026-07-28 window.
**Claim:** When a scheduled routine fails to fire at all, it leaves no negative record anywhere — no checkin, no malfunction, no project doc — because every trace the fleet keys on is written by the routine itself. The tower-sweep loop went completely dark on 2026-07-28 (both daily sweeps missed) and nothing in the registry noticed. The only detector was a *neighboring* loop diffing the log against its own watermark. Absence of evidence became evidence only because a second loop was looking.

## Evidence (paid for in the window)

- Log gap: seq 17528 (previous distillation lands, 2026-07-28T01:05:23Z) → seq 17529 (this fire boards, 2026-07-29T01:01:28Z) — zero entries for ~24 h. No sweep checkin, heartbeat, landing, or seat-boarded event of any kind.
- Baseline: every prior day in the loop's life produced sweep traffic in the same log (e.g. seq 17514/17515 morning sweep on 07-27; seq 17520 evening sweep lands 2026-07-27T21:34Z) and a project doc (`claude/sweep-registry-hygiene-2026-07-23` … `-27b`, daily). No `claude/sweep-registry-hygiene-2026-07-28*` exists.
- Expectation audit score: tower-sweep 2026-07-28 = expectation set (standing daily schedule) and **broken silently** — the worst class, and a new sub-species: not a flight that died, a flight that was never born. `ars_flight_list` cannot show it; there is no row to derive a status from.

## Why it matters

The registry's whole observability model (silent-death detection, malfunction entries, lease expiry) starts at checkin. A schedule miss happens *before* checkin, so the failure class that costs a full day of coverage is precisely the one the machinery cannot record. Today it was caught within 24 h only because the distillation loop happens to audit a watermarked window; if the distillation schedule itself missed, nothing would catch either.

## Suggested landing

Constraint or policy amendment (klappy://ars/policy/morning-meeting-and-pulse adjacent, or durable-flight-registry): every standing scheduled charter gets a declared cadence expectation the registry can check — e.g. a board item carrying `expected_next_fire`, refreshed at each checkin, so `ars_flight_list` reconciliation can surface `missed-fire` the same way it surfaces expired leases. Cheap variant: each scheduled loop's template includes a one-line neighbor check ("did the other loops fire since my last watermark?"), making every loop a watchdog for its siblings — which is exactly what caught this one.
