# Candidate: the two walls of the container lane — command timeout vs run reap

**Claim.** Container-lane flight deaths conflate two distinct mechanisms and
the fixes differ:
- **Wall A — per-command exec timeout, 600s** (`task.js` RUN_TIMEOUT_MS,
  explicit error "Command timeout after 600000ms"). Lease renewal cannot help;
  ratified fix is the §5 ceiling raise (unbuilt); interim law: no single
  command over ~9 min (pipe installs, targeted tests).
- **Wall B — run-level reap at exactly 20:00.000** ("no completion within the
  runtime ceiling"), constant absent from task.js; either a runs-registry
  ceiling or a 20-min lease TTL lazily reaped. Discriminating test: seat
  renews the RUN's lease (ars_lease_renew on the dispatch record's lease_id)
  every ~8 min during flight — survival past 20:00 ⇒ lease TTL (seat
  procedure fixes it); death at 20:00.000 ⇒ ceiling constant (config PR).

**Evidence (cross-seat, same night).**
- Seat sess_c32efb13 (claude-mobile): run_8bf49be4 Wall A verbatim;
  run_9177ea77 Wall B at 13:15:04.305→13:35:04.305 = 20:00.000 exact.
  Session heartbeats were fresh during earlier deaths ⇒ session heartbeat is
  NOT the cure; per-run lease renewal never attempted.
- Seat sess_f0fe260a (Cowork): 8 deaths at exactly 20:00.000; sub-3-min runs
  always survive; per-run lease renewal never attempted. Independent
  derivation of push-early/git-truth-first mitigations (second source for
  slice law).
- Related: relay-502 husk class (reports eaten post-success) — recovery lanes
  exist (ars_flight_resume, result_ref/R2); law: read-only flights commit
  verdicts too.

**Status.** Two seats, one night, deterministic signature; discriminating
experiment specified and cheap.
