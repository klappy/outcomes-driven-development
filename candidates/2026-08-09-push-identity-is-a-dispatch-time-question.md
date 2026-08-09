# Push identity is a dispatch-time question — a run that must decide whose name goes on the commit will sometimes refuse instead

**Seed class:** candidate constraint — distilled by the nineteenth scheduled distillation fire, 2026-08-08 (ET civil date; fired 2026-08-09T01:01Z UTC).

**Claim:** The gauntlet-amendment execution chain (this window, 01:43–02:10Z on 08-08) made three attempts and delivered nothing. The terminal run, run_50de71a1, refused on new grounds: "Repo is unchanged — I only ran read-only checks… I'm not doing the push," citing a shared-branch push under a named identity as its reason. That is a third distinct refusal class now on record — after injection-refusal (PR #46 seed #1: fresh contexts refuse authentic briefs whose authority is only claimed in-band) and harness permission-denial (run_4cf24825, Write auto-denied). All three share a root: the brief left a legitimacy question for the run to resolve at execution time, and a conscientious fresh context resolves unverifiable legitimacy by stopping. Attribution doctrine exists (operator no-reply author, assign-don't-request-review) but lives in tooling docs, not in the brief contract — so each run re-derives, and sometimes re-litigates, whose name goes on the push.

## Evidence
- run_d2fd4f15 (01:43Z): relay 502, honest loud block, superseded by explicit re-dispatch — the chain's one clean failure.
- run_4cf24825 (01:58Z): Write tool auto-denied by permission mode; stopped; nothing pushed — yet status landed, board done.
- run_50de71a1 (02:10Z): identity-grounds refusal quoted above; nothing pushed — yet status landed, board done. No later flight with a matching brief exists (sweep probes: brief_contains "gauntlet" → 1 row; "amended canon file pushed" → 3 rows, all in-chain).
- Source of record: claude/sweep-registry-hygiene-2026-08-08.md (sess_3de8c281, full registry snapshot 12:44Z).

**Corroboration, not a duplicate seed:** fl-4cf24825 and fl-50de71a1 reading board-done with undelivered cargo is the third consecutive observation of the landed-with-refusal-cargo pattern (escrow-hold chain 08-07, PR #44/#46) — filed here as additional evidence for open PR #44, which already carries that seed.

## Proposed canon shape
Constraint: an execution brief that requires a push declares, in the brief itself, the push identity (author/committer email per attribution doctrine), the branch-sharing posture (whose branch, who else writes to it), and the authority pointer for both — so identity is settled at dispatch, checkable out-of-band, and never a run-time judgment call. A push-charter without the identity block is uncrewed, the same way a brief without the lifecycle spine is. Complements PR #46 seed #1 (out-of-band provenance) — this is the same principle applied to the write path instead of the read path.
