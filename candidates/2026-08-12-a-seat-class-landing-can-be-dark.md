---
kind: candidate
type: observation
title: "A seat-class landing can be dark — checkout without a debrief leaves no history in the log"
date: 2026-08-12
status: candidate
source_flights: ["sess_7c9b1ffe-527a-4bc7-b8e8-c80d93104cff"]
evidence: "ars_log seq 33131–33132: seat-boarded 2026-08-11T21:34Z (tool cowork-scheduled-sweep) then flight-landed 21:35Z with NO flight-recorded entry between them. The work's only record is the project doc claude/sweep-registry-hygiene-2026-08-11b.md — outside the log."
epoch: E0010
---

# A seat-class landing can be dark

## Observation

The evening sweep of 2026-08-11 (sess_7c9b1ffe) boarded as a seat, did its
work, and checked out `landed` — with no debrief. The append-only log shows
`seat-boarded` → `flight-landed` and nothing in between (seq 33131–33132).
The recorder gate only guards flight-class sessions; a seat-class checkout
walks past it, so the registry records a landing with no history.

The work itself was not lost — a durable project doc exists
(`claude/sweep-registry-hygiene-2026-08-11b.md`) — but the log cannot see
it. An auditor reading only the registry finds a landing that delivered
nothing. This is a quieter cousin of the silent death: not a flight that
died without a debrief, but one that *landed* without one.

## Candidate lesson

A durable artifact outside the log is not a debrief. Scheduled seats that do
real work should volunteer a debrief at checkout even when the recorder gate
does not force it — the gate is a floor, not the standard. Expectation set
and kept in the world, but broken in the record, still breaks the audit.
