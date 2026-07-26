---
status: candidate
kind: observation
date: 2026-07-26
source: "distillation flight sess_9fc6712e (2026-07-26, scheduled third loop)"
derives_from: "klappy://canon/values/trust-kernel, klappy://ars/policy/durable-flight-registry"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md)"
evidence: "ars_session_list(role=cdo) 2026-07-26T01:03Z returns sess_087ad253 and sess_0897ffe0 with full rows and debriefs; ars_flight_list (361 rows, truncated:false, include_seats both ways) omits them and every other LANDED seat-class session; PR #32 seed scored these same flights as never-registered"
---

# The Flight Registry Is Blind to Landed Seats

**Observation.** Yesterday's distillation (PR #32) scored sess_087ad253 and
sess_0897ffe0 as silent deaths of the record — "no row, no seed, nothing was
ever written." Today the registry contradicts that: `ars_session_list`
returns both sessions with complete rows and volunteered debriefs. They were
registered all along. The audit surface, `ars_flight_list` — advertised as
"THE durable flight registry ... replacing the ephemeral harness session
list entirely" — omits landed seat-class sessions even with
`include_seats:true` (that flag surfaces only currently-seated rows). The
audit was blind, not the record.

**The gap.** An audit that trusts one projection inherits that projection's
blind spots and then legislates from them: PR #32 proposes a standing rule
built on evidence this window falsified. A distillation that mis-scores
honest, debriefed flights as silent deaths spends trust in both directions —
against the flights it defamed and against the seeds it filed.

**Proposed rule.** The registry surface must show landed seats, or must say
it does not. Until then: any audit that scores a flight as unregistered must
cross-check `ars_session_list` before writing the verdict, and PR #32's
first seed should be amended at merge time — the observed failure was
projection blindness, not a phantom checkin.
