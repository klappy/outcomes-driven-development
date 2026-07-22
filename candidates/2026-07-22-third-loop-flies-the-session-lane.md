# Candidate: the third loop flies the session lane — long-form charters die on the container lane

**Seed class:** observation → constraint. Drafted by the first completed scheduled distillation debrief (sess_3c6643b2, 2026-07-22, Cowork scheduled lane).

**Claim.** Until run-completion durability ships (ARS PRD #112), any long-horizon or long-form-authoring charter — the daily distillation debrief above all — flies a session lane (scheduled Cowork seat), never `ars_task_run` on the container lane. The lane ruling is not preference; it is the difference between the loop existing and not existing.

## Evidence (paid for, in-window 2026-07-15 → 2026-07-22)

- Five consecutive container-lane distillation charters died without landing (runs fb133d81, 8bf49be4, 7efeae98, 9177ea77, 97e78310; 2026-07-20/21 — cited from the dispatch record; the registry page returned to this flight was truncated before them, itself an audit finding). The third loop therefore never ran before today.
- Two more long-form container runs were reaped run-lost on 2026-07-22 alone: run_1b7abef4 (execution: charter document; malfunction run-lost at 23:19:35Z) and run_128a0cbc (planning: docs/prd/work-source-adapter-v1.md; run-lost at 21:57:49Z, no heartbeat ever recorded).
- First completion of the scheduled distillation happened today, on the session lane, same charter, no code change — the lane was the variable.

## Relation to existing seeds

`candidates/2026-07-20-two-walls-of-the-container-lane.md` names the mechanisms (600s exec timeout; 20:00.000 run reap). This seed adds the routing law those walls imply: don't send work through a door that is known to close on it. Sunset condition: when #112 (run-completion durability) lands and a container-lane long-form run demonstrably survives, this constraint is re-validated or retired — per the third-loop sunset review.
