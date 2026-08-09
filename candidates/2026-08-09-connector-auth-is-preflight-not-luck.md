# Connector credentials rot between scheduled fires — auth is a preflight check, and durable docs are the fallback ledger by design

**Seed class:** candidate constraint — distilled by the nineteenth scheduled distillation fire, 2026-08-08 (ET civil date; fired 2026-08-09T01:01Z UTC).

**Claim:** The ARS MCP connector lost its authorization sometime between the 2026-08-08T12:44Z tower sweep (sess_3de8c281, ARS fully reachable) and the 21:33Z sweep firing, which found it in needs-auth state on a non-interactive lane and correctly declared NO-GO (claude/sweep-registry-hygiene-2026-08-08b.md). This distillation fire, ~3.5 hours later, found ARS still unauthorized and flew the whole window degraded — no ars_flight_list, no ars_log_read, no checkin/checkout, window audit reconstructed entirely from durable project docs. Two scheduled charters on one civil day were degraded by a single silent credential loss that no system observed until a charter died on it. Credential expiry is rotation for minted flight tokens (klappy://ars/policy/seat-minted-flight-credentials) — but connector-level OAuth on the scheduled lane has no equivalent doctrine: it rots silently, and only an interactive session can restore it.

## Evidence
- sess_3de8c281 sweep, 12:44–12:46Z: full ars_flight_list snapshot taken, board_brief read — ARS healthy (claude/sweep-registry-hygiene-2026-08-08.md).
- 21:33Z sweep: "ARS connector unauthenticated in this scheduled session… non-interactive, so ars_session_checkin, ars_flight_list, board_brief, and parity_check were all unreachable" — NO-GO, zero registry assertions made (claude/sweep-registry-hygiene-2026-08-08b.md).
- This fire, 2026-08-09T01:01Z: ARS still needs-auth (harness-confirmed); distillation flew from the two sweep docs above plus claude/distillation-2026-08-08.md as watermark.
- Validation of a prior seed: PR #46 seed #2 proposed time/registry-anchored watermarks with durable docs as backstop after log pruning outran the seq watermark. This window proved the backstop under a *different* failure (auth loss, not pruning): the durable-doc trail alone was sufficient to fly a degraded but honest audit.

## Proposed canon shape
Constraint, two clauses. (1) Every scheduled charter probes its required connectors at boarding, before the window burns; an unreachable required connector is a loud NO-GO with a captain flag, never a silent partial flight — asserting registry state you could not observe violates Axiom 4. (2) Each scheduled charter names its durable-doc fallback ledger (for this loop: the sweep and distillation project docs) so a degraded fire has a declared, auditable evidence base rather than an improvised one. The 08-08b sweep already flew clause 1 correctly by instinct; this seed asks to make it law.
