---
kind: candidate
type: observation
title: "The sweep's cadence drift is a duplicate schedule — two lanes now fire the same charter daily"
date: 2026-08-12
status: candidate
source_flights: ["sess_836404df-9759-4646-86a1-689af141bbe5", "sess_7c9b1ffe-527a-4bc7-b8e8-c80d93104cff"]
evidence: "ars_log seq 33128 (seat-boarded 2026-08-11T12:06Z, harness worker-cron, tool cowork-scheduled-sweep) and seq 33131 (seat-boarded 2026-08-11T21:34Z, harness cowork, same tool). Two sweep firings on one civil day, on two different harnesses. Prior window (PR #49 seed) read the 21:33Z firings as the morning lane drifting; this window shows both lanes live simultaneously."
epoch: E0010
---

# The cadence drift was a duplicate schedule

## Observation

PR #49's seed read the sweep's evening firings as cadence drift — the
morning lane gone dark, replaced by an evening one. The 2026-08-11 window
falsifies that reading: the sweep fired at 12:06Z on `worker-cron` AND at
21:34Z on `cowork`, same charter, same day. Both lanes are live. What
looked like a shifted schedule is a duplicated one.

The cost is not just double spend. Two schedules for one charter means no
single declared expectation to audit the fire times against — either lane
missing looks like drift, both firing looks like noise, and the doubled
evening run landed dark (see companion seed).

## Candidate lesson

One charter, one schedule. When a scheduled expectation appears to drift,
check for duplication before rescheduling — the fix for a duplicate is
deletion, not adjustment, and every added lane subtracts auditability.
Captain action: identify and retire one of the two sweep schedules.
