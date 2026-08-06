# The debrief channel is not a cargo hold — artifacts land in durable storage, records carry pointers

**Seed class:** candidate constraint — distilled by the sixteenth scheduled distillation fire (sess_cc610493), 2026-08-05 (captain civil date; UTC 2026-08-06T01:02Z).

**Claim:** On 2026-08-05 the cooking-taxonomy artifact produced by run_ad290ff1 was too large for one run-return, so the dispatcher (sess_78b50062, cowork-mobile) retrieved it in three chunked container runs (run_2a9a96e9, run_89b6896e, run_5e390565, plus earlier retrievals). Each chunk came back as the run's *debrief summary* — and because board resolution derives its note from the debrief, verbatim document fragments ("## 4. Role Reconciliation…", "## 7. Mapping to Existing Machinery…") are now permanently written into the coordination log as flight-recorded debriefs and board-item-resolved attestation notes (seq 22617–22618, 22845–22846, 24469–24470). The record channel — meant to answer "what happened to this flight?" — was used as a data bus, so the flight registry now carries page-fragments of a taxonomy doc where its history should be. The chunked-retrieval workaround itself worked (all runs landed); the failure is where the cargo landed.

## Evidence
- seq 22617 / 22618: flight-recorded + board-item-resolved for run_2a9a96e9 — debrief summary and attestation note are verbatim document body ("## 4. Role Reconciliation (March → August)…").
- seq 22845 / 22846: same pattern for run_89b6896e ("## 7. Mapping to Existing Machinery…").
- Dispatch preflight receipts name the pattern explicitly: "chunked retrieval of run_ad290ff1 artifact, part 2 of 3 / part 3 of 3" (seq 22615, 22843).
- Contrast: the artifact chain's own validation run (run_70567c39, VERIFIED-WITH-FINDINGS) and correction (run_4b7cc642, v3, sha256 0fa7b2e0…) show the crew *could* address content by hash — the durable home existed; retrieval just routed around it.

## Proposed canon shape
Constraint: a run's product larger than a paragraph lands in durable storage (repo path, R2 object, project doc) and the debrief carries the pointer plus the hash — never the body. A debrief whose summary is the cargo is a recording failure even when the run status is done: it pollutes the board's resolution notes, bloats the append-only log, and leaves the artifact scattered across N flight records with no single authoritative copy. Corollary for dispatchers: if the return channel is too small for the artifact, the fix is "write to a durable home and return the pointer," not "chunk the artifact through more debriefs."
