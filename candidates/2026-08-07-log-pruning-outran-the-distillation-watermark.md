# Log pruning outran the distillation watermark — a seq-based watermark is only as durable as the log's retention

**Seed class:** candidate constraint — distilled by the eighteenth scheduled distillation fire (sess_f6c8bf94), window 2026-08-07.

**Claim:** The previous distillation (sess_83eced26) set its watermark as "log seq > 24479." When this fire tried to read the window, the log answered `truncated_before: 29504` — bulk task-run pruning on 2026-08-07 (thousands of `task-run-pruned` entries written 19:57–20:16Z) had consumed and truncated everything between the watermark and mid-evening. Roughly eighteen hours of the window (01:02Z–19:35Z) were dark to the log-as-truth surface; the day's cooking-taxonomy v5 chain was recoverable only via the durable flight registry and the tower-sweep project doc. The system's own axiom — you cannot verify what you did not observe — was almost violated by the system's own hygiene: the audit trail's retention policy and the audit cadence were not coordinated.

## Evidence
- claude/distillation-2026-08-07.md: "Next watermark: this flight's checkout (log seq > 24479)."
- ars_log_read(after_seq=24479) on 2026-08-08T01:03Z: `truncated_before: 29504`, first readable entries are the prune batch itself.
- Window reconstruction required fallback to ars_flight_list (durable registry) plus claude/sweep-registry-hygiene-2026-08-07.md — which is the registry doing its designed job, but the log's window was unrecoverable.

## Proposed canon shape
Constraint (two-sided): (a) the distillation watermark is time- and registry-anchored, not seq-anchored — "flights since <ISO timestamp>, cross-checked against the durable registry" survives pruning; a bare seq does not; (b) log pruning must retain at least one full audit cadence (the distillation interval plus margin) of non-noise entries, or write prune summaries that preserve the pruned entries' landing facts. The registry-as-fallback worked this time; the constraint makes it not a matter of luck.
