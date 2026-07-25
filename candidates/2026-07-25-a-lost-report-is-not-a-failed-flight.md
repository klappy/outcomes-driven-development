---
status: candidate
kind: constraint
date: 2026-07-25
source: "distillation flight sess_5aca9b25 (2026-07-25, scheduled third loop)"
derives_from: "klappy://canon/values/axioms (Axiom 1, Axiom 3), klappy://ars/policy/durable-flight-registry"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md)"
evidence: "run_feffd2ea (2026-07-24T18:31Z) and run_70984ae6 (17:45Z): task status 'succeeded', report fetch 502 → machine-drafted debrief outcome 'blocked'; the 18:41 validator brief names PR 212 / fix/github-auth-fetches, which only exists if run_feffd2ea pushed it (sweep claude/sweep-registry-hygiene-2026-07-24b.md)"
---

# A Lost Report Is Not a Failed Flight

**Constraint.** When a run's execution status and its report retrieval
disagree, the recorder must not collapse the ambiguity into "blocked."
Twice on 2026-07-24 a container run finished with task status `succeeded`,
the runtime report fetch returned 502, and the machine-drafted debrief
recorded the flight as **blocked**. In at least one case (run_feffd2ea) the
work demonstrably landed — the branch it was chartered to push is named by
the very next validator brief. The ledger now asserts the opposite of
reality.

**Why it matters.** A false "blocked" is the mirror image of a false "done"
(Axiom 3) and is operationally worse than an honest unknown: it invites
re-dispatch of finished work, hides real landings from the metric, and
corrupts every downstream audit that trusts the registry.

**Proposed rule.** The machine recorder distinguishes three outcomes, not
two: execution failed → `blocked`; execution succeeded but report
unretrievable → a distinct `landed-unrecorded` (or `unknown`) outcome
carrying the runtime status as evidence; both healthy → the debrief as
written. Anything that sweeps or re-dispatches treats `landed-unrecorded`
as "verify before re-flying," never as free-to-retry.
