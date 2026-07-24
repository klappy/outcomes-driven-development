# A gate with no live lane converts honest work into blocked debt
**Seed class:** candidate — observation (constraint if repeated), distilled by the scheduled distillation flight, 2026-07-24.
**Claim:** The validation gate is only as strong as the weakest AVAILABLE validation lane. When every lane is down, the gate does not stop bad work — it strands good work: honest flights check out `blocked` with the deliverable already shipped, and the owed re-validation becomes queue debt nobody is leased to. Validation-lane availability should be a preflight item for any flight whose landing requires a fresh-context verdict.

## Evidence (window 2026-07-23T01:10Z → 2026-07-24T01:00Z)
- sess_28aefca0 (charter-cv-coo-demo F2): deliverable shipped (commits ed33915 + fb1a5b0 on demo/2026-07-23-coo-demo), then tried THREE validation lanes and all failed — API lane 503 (ANTHROPIC_API_KEY not provisioned), container validators run_28e0861c and run_5ae4d1a7 both reaped run-lost (13:06Z, 13:25Z, intermittent 502s at the runtime ceiling), no local subagent tool in that harness. Checked out `blocked` on the gate alone. Integrity held (axiom 3); throughput did not.
- Precedent from the prior window: run_ecb80336, container-lane validator, lost 2026-07-23T01:05Z (distillation-2026-07-22b, ODD PR #29 "a fixed cause is not a fixed lane").
- Contrast, same window: when the container lane held, the gate worked exactly as designed — run_5da0f749 and run_dedd2dd8 returned PASS and four G5 merges landed VERIFIED (covenynt/chief-operating-officer PRs #3–#6).

## Proposed mechanism
A validation-requiring charter's preflight verifies at least one validation lane is live (cheap ping) before launch; if none is, the dispatch is deferred, not flown into a guaranteed block. The owed-re-validation backlog (fl-28aefca0 today) gets a named owner at sweep time.
