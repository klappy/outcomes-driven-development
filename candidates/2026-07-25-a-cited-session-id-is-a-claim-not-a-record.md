---
status: candidate
kind: observation
date: 2026-07-25
source: "distillation flight sess_5aca9b25 (2026-07-25, scheduled third loop)"
derives_from: "klappy://canon/values/trust-kernel, klappy://ars/policy/durable-flight-registry"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md)"
evidence: "ars_flight_resume sess_087ad253 → not-registered; ars_flight_resume-equivalent absence of sess_0897ffe0 in ars_flight_list (360 rows, truncated:false, 2026-07-25T01:01Z)"
---

# A Cited Session ID Is a Claim, Not a Record

**Observation.** The 2026-07-24 distillation flight signed its deliverables
"sess_087ad253" (PR #30, journal entry, project doc), and the 2026-07-24
evening tower sweep signed "sess_0897ffe0". Neither id exists in the ARS
flight registry: `ars_flight_resume` returns `not-registered` — no row, no
seed, nothing was ever written. Both flights delivered real work, and both
flew invisible to the very audit surface one of them was auditing. The
registry caught all 7 container runs in the same window and missed all of
the scheduled seats.

**The gap.** A session id printed in prose feels like proof of registration.
It is not — it is an unverified claim (Axiom 2: a claim is a debt). Either
the checkins never happened and the ids are local fictions, or the writes
were lost; from the record alone we cannot tell, which is exactly the
problem.

**Proposed rule.** A flight that intends to be audited verifies its own
registration before citing its id: after checkin, resolve your own id
against the registry (`ars_flight_resume` on yourself, or confirm your row
in `ars_flight_list`) and only then sign deliverables with it. The daily
distillation adds a standing check: every session id cited in the window's
deliverables must resolve to a registry row; a non-resolving id is scored as
a silent death of the record even when the work landed.
