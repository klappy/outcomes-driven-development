# "Done" on the board is a claim, and a claim is a debt — it requires a landed flight as evidence

**Seed class:** candidate constraint — distilled by the twelfth scheduled distillation fire (sess_8b89b5e8), 2026-08-02.

**Claim:** Board item `tataoro-cafe-admin-dashboard-v1` was marked done while both of its bound runs were dead — run_b1a1a431 failed (sandbox command timeout, seq 19251) and run_37686140 machine-recorded truly lost (seq 18816) — and no flight ever landed against it. The 2026-08-01 tower sweep (sess_17c5717f) caught the drift and filed a captain flag, which is the system working at the audit layer; but the write itself should not have been possible without proof. Axiom 2 (A Claim Is a Debt) already binds sessions at checkout via the recorder and validation gates. Board resolves to done currently carry no equivalent gate: a seat can assert done with nothing behind it, and the lie sits on the captain's curated surface until a sweep happens to look.

## Evidence
- seq 18200 (2026-08-01T03:28Z): board-item-upserted `tataoro-cafe-admin-dashboard-v1` by sess_6b28ad16, which then never checked out.
- seq 18816 / 19251: both bound runs dead (one truly lost, one failed on timeout — the container lane's known walls, see PR #38/#39 candidates).
- sess_17c5717f sweep debrief (seq 19264): "tataoro-cafe-admin-dashboard-v1 marked done with no landed flight and both bound runs dead — GitHub unverifiable from scheduled lane."

## Proposed canon shape
Constraint: a board resolve to ✅ done must carry at least one proof pointer that resolves to a landed flight (flight-recorded debrief) or captain-authored ruling; a done-resolve without one is refused at the door, the same way checkout refuses a landing without a debrief (RECORDER_REQUIRED) or a VERIFIED validation receipt. The sweep stays as backstop, not as the gate. This extends the existing lifecycle symmetry: sessions already cannot claim landed without proof — items should not be able to claim done without a landing.
