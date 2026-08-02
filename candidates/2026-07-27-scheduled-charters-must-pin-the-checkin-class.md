# Scheduled charters must pin the checkin class — or the lifecycle gates silently don't apply

**Seed class:** candidate constraint — drafted by the sixth scheduled distillation fire (sess_fc1915fd), 2026-07-27.

**Claim:** ARS lifecycle gates (preflight, lease, recorder, validation) bind flight-class checkins only; seat-class landings may close with no validation receipt at all. A scheduled routine's charter that does not pin `class: flight` leaves the gate coverage to each fire's improvisation — so the same charter fires audited one day and unaudited the next, and the expectation-audit surface degrades without anyone deciding it should.

## Evidence (all in-window, 2026-07-26T01:07Z → 2026-07-27T01:02Z, ars log seq 17500–17511)

- Same sweep charter, same day, different gates: morning sweep sess_a7b64121 landed `validation: null` (seq 17501); evening sweep sess_f7afbf0d landed with a fresh-context VERIFIED receipt plus board item, lease, and preflight (seq 17503–17510). Nothing in the door forced either choice — the delta is the session's own checkin class and initiative.
- Same drift in the distillation family: the 07-25 and 07-26 fires boarded flight-class with preflight + lease (seq 17483–17485, 17492–17496); this 07-27 fire boarded seat-class (seq 17511) because the charter text does not pin the class. The work still lands, but the launch gate, lease, and VALIDATION_REQUIRED checkout door were all voluntarily rather than structurally applied.

## Proposed mechanism

Every scheduled charter (distillation, tower sweep, future routines) carries an explicit boarding line: `checkin class: flight, preflight receipt required` — so gate coverage is a property of the charter, not of the individual fire's memory. A seat-class landing by a scheduled routine then becomes an auditable deviation instead of an invisible default.

## Relation to existing canon

Extends klappy://ars/policy/durable-flight-registry (the gates exist) and PR #33 seed 2 (paid-for workarounds must transfer to sibling routines): this is the same transfer failure one level up — not a workaround but the gate discipline itself failing to transfer between fires of the same routine.
