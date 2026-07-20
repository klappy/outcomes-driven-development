---
status: candidate
date: 2026-07-20
source: "incident during the 2026-07-19 evening → 2026-07-20 morning shift"
attribution: "distilled by the closing seat from the PR #306 recovery"
derives_from: "klappy://canon/values/trust-kernel — an assumed receipt is a promise the seat made to itself without evidence"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md) — awaiting distillation sweep; promotion is the captain's merge alone"
---

# Destructive Cleanup Awaits the Observed Receipt

**Single-incident evidence — flagged as such.** This seed names a pattern
observed once this shift; it is recorded because the mechanism it proposes
is general, not because the incident count clears an independence bar.

## The incident

The seat deleted a PR branch as routine cleanup before observing the merge
receipt for the work that branch carried. GitHub auto-closed the captain's
PR #306 as a side effect of the branch deletion — the cleanup action fired
in the same breath as the action it was meant to follow, and the ordering
inverted. Recovered in seconds once noticed, no lasting damage.

## The proposal

Law: destructive cleanup never shares a command block with the action it is
meant to follow. It waits for the **observed** receipt — the merge SHA, the
closed-and-merged state actually read back, not merely assumed because the
prior step "should have" succeeded — before it runs. Batching a destructive
step with its trigger action optimizes for fewer round-trips at the cost of
making the destructive step blind to whether its precondition actually
held.

## Evidence

One incident (PR #306, this shift). No cross-session recurrence yet
observed. Recorded because the failure mode (destructive command batched
with the action it depends on) is a general shape, not because this
instance alone establishes a pattern.

## Open question for ratification

Whether this becomes a hard rule (never batch) or a default-with-override
(batch only when the precondition is independently guaranteed, e.g. by a
prior gate) is not resolved here.
