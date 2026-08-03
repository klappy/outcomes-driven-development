# A scheduled charter flown seat-class lands dark in the registry

**Seed class:** candidate observation — distilled by the thirteenth scheduled distillation fire, 2026-08-03.

**Claim:** The 2026-08-02 evening tower sweep (sess_7759970e, tool cowork-tower-sweep) boarded seat-class at 21:34:05Z and landed one log row later (seq 19732 → 19733) with no debrief, no proof pointers, and no recorder entry in the registry. The sweep DID its work — the durable record exists as project doc claude/sweep-registry-hygiene-2026-08-02b.md, verdict CLEAN — but the flight registry, the machine-truth ledger, shows only boarded-then-landed. Seat-class checkout bypasses the recorder and validation gates by design (interactive seats), and a scheduled charter that boards seat-class inherits that exemption it was never meant to have. Anyone auditing from ars_flight_list alone would read an empty landing; the record lives only on a side surface the registry does not point to.

## Evidence
- seq 19732: seat-boarded sess_7759970e (harness cowork-scheduled, tool cowork-tower-sweep).
- seq 19733: flight-landed, leases_released [], no flight-recorded row between.
- Project doc claude/sweep-registry-hygiene-2026-08-02b.md: the actual sweep record (tallies, verdict, proof) — reachable only if you already know where to look.
- Contrast: the morning sweep sess_9c03aff4 boarded flight-class and its debrief is in the registry (seq 19725), VERIFIED.

## Proposed canon shape
Observation: a session launched by a schedule is dispatched work, not an interactive seat — it should board flight-class (dispatch_brief + preflight) so the recorder and validation gates apply and its record lands in the registry, not only in a side document. Corollary for the door: a checkin whose tool/harness names a scheduled charter (cowork-scheduled, cowork-tower-sweep) declaring class seat is a signed, auditable claim the audit should surface.
