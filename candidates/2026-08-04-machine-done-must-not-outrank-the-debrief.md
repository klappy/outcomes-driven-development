---
kind: candidate
type: constraint
title: "A machine 'done' must not outrank the flight's own debrief"
date: 2026-08-04
status: candidate
source_flights: ["run_60791523", "fl-60791523"]
evidence: ["ars log seq 21704-21706", "claude/sweep-registry-hygiene-2026-08-04.md"]
drafted_by: "sess_130552bf (scheduled distillation, 2026-08-05)"
---

# A machine "done" must not outrank the flight's own debrief

## Observation (paid for)

Container run run_60791523 (2026-08-04, PR-93 refresh) finished with exit
`ok:true`, and the machine-drafted close resolved its board item fl-60791523
`active → done` (seq 21706). But the run's own debrief text — written in the
same event — says plainly: "I could not open the PR, so this attempt is
incomplete" (seq 21705). The board now asserts done; reality is a pushed
branch (`refresh/pr-93-2026-08-04`) with no PR. The evening sweep
(sess_fbda5cfd) caught the contradiction only by reading the debrief prose
against the resolution.

## Candidate constraint

When a landing is machine-drafted, the resolution must be derived from the
debrief's declared outcome, not from the process exit code. A debrief that
self-declares incompleteness, a blocker, or an owed deliverable resolves the
item to blocked / needs-captain — never to done. `ok:true` means the process
exited; only the debrief says whether the expectation was kept. A board
"done" that contradicts the flight's own words is a false claim written by
the machinery itself — the worst place for one, because no one is lying and
everyone downstream is misled.

## Why (trust kernel)

A claim is a debt (Axiom 2). The machine-drafted close currently mints
claims with no evidence check, so the registry — the surface built to keep
expectations auditable — becomes the source of the broken expectation.
