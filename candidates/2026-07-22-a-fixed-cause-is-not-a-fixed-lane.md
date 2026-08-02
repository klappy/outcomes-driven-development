# Candidate: a fixed cause is not a fixed lane — retries inherit the lane's casualty risk

**Seed class:** observation. Drafted by the second completed scheduled distillation debrief (sess_d7ab9a48, 2026-07-22 evening ET, Cowork scheduled lane; first on-schedule fire of trigger `0 1 * * *` UTC).

**Claim.** Fixing the diagnosed cause of a dead flight and re-dispatching on the same lane treats the diagnosis as the whole risk. It is not: the lane carries its own casualty rate, independent of the fixed cause. A retry decision must weigh the lane's record for that flight class, not just the postmortem of the single predecessor. Concretely, until run-completion durability ships (ARS PRD #112), validation-mode charters join long-form charters under the session-lane routing of `candidates/2026-07-22-third-loop-flies-the-session-lane.md`.

## Evidence (paid for, in-window 2026-07-22T23:29Z → 2026-07-23T01:05Z)

- run_ecb80336 (seat `adapter-prd-validate`, container lane, item fl-128a0cbc) was the retry of run_a39e1302, which blocked when its git token expired before container boot. The retry's preflight fixed exactly that: fresh read-only token minted expiring 00:04Z, "all other preflight items unchanged" (log seq 14063, dispatched 23:02:30Z).
- The retry never boarded — session_id null, no heartbeat ever recorded — and was machine-reaped run-lost at 01:05:05Z with no debrief (log seqs 14080–14081). Broken silently: the worst class, and the only flight death in this window.
- Item fl-128a0cbc's validation has now died on the container lane under two different causes (token expiry, then run-lost with the token fixed). The variable that did not change across both deaths is the lane.

## Relation to existing seeds

`2026-07-22-third-loop-flies-the-session-lane.md` routes long-form charters off the container lane; `2026-07-20-two-walls-of-the-container-lane.md` names the mechanisms. This seed adds the retry corollary: a casualty's postmortem scopes the fix, but the re-dispatch decision must also consult the lane's history for that flight class — otherwise each retry pays the same tuition under a new cause label. Sunset: same as the session-lane constraint — re-validate when #112 lands.
