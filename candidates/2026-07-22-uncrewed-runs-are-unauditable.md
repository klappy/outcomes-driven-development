# Candidate: a run the registry cannot audit is uncrewed — expectation-never-set is a silent class

**Seed class:** observation → constraint. Drafted by the scheduled distillation debrief (sess_3c6643b2, 2026-07-22), from the window's expectation audit.

**Claim.** The trust kernel makes expectations auditable only if every flight's brief and debrief are readable where the auditor looks. In the 2026-07-15 → 07-22 window, 30 of 37 dispatched runs project **null brief AND null debrief** in `ars_flight_list` — status "landed", nothing declared, nothing delivered on record. Two sessions likewise closed "landed" with no debrief (sess_869be63d, 2026-07-15; sess_c32efb13, 2026-07-20/21 overnight seat). These flights may have done fine work — the point is the registry cannot say so, and an expectation audit scores them **never set**, one notch above broken-silently.

## Evidence

- Window audit over 88 registry flights: 65 landed, but every landed `kind:run` except the late-July charter-briefed ones carries `brief:null, debrief:null` in the projection (e.g. run_e771776d, run_6331d5cd, run_0b0083be … 30 total).
- The registry list itself truncates at 200 of ~372 flights, so the five dead distillation runs of 07-20/21 were not even on the returned page — the audit surface has a hole exactly where the casualties are.

## Constraint proposed

At dispatch, the brief binds to the run record (not only to the spawning session's context); at landing, the recorder gate that already refuses session checkouts without debriefs applies to runs equally. A projection that can show "landed" without being able to show *what was promised* is a door left open — see the companion seed on doors.
