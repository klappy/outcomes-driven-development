# A duplicate checkin leaves a phantom twin (silent-death class)

**Seed class:** candidate observation — drafted by the scheduled distillation seat (third loop), 2026-07-27 window.
**Claim:** When a scheduled fire's checkin lands twice (retry, duplicate delivery, or double invocation), the registry gains a twin seat that nothing owns. The working twin lands with a debrief; the phantom twin never checks out and becomes a silent death — the worst expectation class — with no malfunction it earned, because it never did or promised anything. Boarding should be idempotent per fire, or the sweep template should recognize the sub-second twin signature and fold it into the working flight's record instead of carrying a permanent silent casualty.

## Evidence (paid for in the window)

- Log seq 17514: `seat-boarded` sess_7b04c82e, 2026-07-27T13:45:02.341Z, tool `cowork-tower-sweep`.
- Log seq 17515: `seat-boarded` sess_a449a4e1, 2026-07-27T13:45:02.630Z — same tool, same role, same harness, 289 ms later.
- Seq 17516–17517: sess_a449a4e1 records its debrief and lands (project doc claude/sweep-registry-hygiene-2026-07-27.md). sess_7b04c82e appears nowhere again: no heartbeat, no debrief, no checkout, through end of window (seq 17520) and into the next fire.
- Expectation audit score: sess_7b04c82e = never set, broken silently. Seat-class boarding carries no brief, so no gate ever notices it.

## Why it matters

The registry's silent-death detection keys on leases and briefs; a brief-less seat twin evades both. Every such twin inflates the seated/lost tallies the tower sweeps audit, and each one costs a future sweep an investigation to conclude "nothing was lost" — attention spent on an artifact of delivery semantics, not on work. The fix is structural (idempotency key on checkin per scheduled fire, or twin-signature recognition in the sweep template), not vigilance.

## Suggested landing

Constraint or sweep-template amendment in ARS policy (docs/policy/ or klappy://ars/policy/dispatch-seat-guard adjacent): scheduled charters that board a seat should carry a fire-unique idempotency token, and sweeps should classify a <1s same-tool twin with zero subsequent events as `duplicate-boarding`, folded, not lost.
