# A filed candidate governs nothing until promoted — the failure it names repeats on schedule

**Seed class:** candidate observation — distilled by the fourteenth scheduled distillation fire, 2026-08-04.

**Claim:** On 2026-08-03 the thirteenth distillation filed candidate seed "a scheduled charter flown seat-class lands dark in the registry" (ODD PR #42, citing sess_7759970e, seq 19732–19733). Twenty hours later, before that PR was merged, the same scheduled evening sweep repeated the exact failure the seed names: sess_503e485c (harness worker-cron, tool cowork-scheduled-sweep) boarded seat-class at 2026-08-03T21:33:41Z and landed one row later (seq 19737 → 19738) with no debrief, no proof pointers, no recorder entry in the registry. The sweep again did its work — project doc claude/sweep-registry-hygiene-2026-08-03.md, verdict CLEAN SWEEP — and the registry again shows only boarded-then-landed. A lesson written into a candidates/ branch changes no behavior: the schedules that produce the failure keep firing with their old prompts while the seed waits for promotion.

## Evidence
- seq 19737: seat-boarded sess_503e485c (worker-cron, cowork-scheduled-sweep), 2026-08-03T21:33:41Z.
- seq 19738: flight-landed, leases_released [], no flight-recorded row between — identical shape to seq 19732–19733 one day earlier.
- ODD PR #42 state at 2026-08-04T01:02Z: open, merged:false — the seed naming this failure was on file but not yet law when the failure recurred.
- Project doc claude/sweep-registry-hygiene-2026-08-03.md: the sweep's actual record, again only on a side surface the registry does not point to.

## Proposed canon shape
Observation: distillation closes the loop only at promotion, and promotion closes it only when the offending charter is amended. When a candidate names a failure produced by a *recurring schedule*, the seed alone is a prediction that the failure will recur — and it did, within one day. Corollary for the loop: a candidate that indicts a scheduled charter should carry, and its promotion should trigger, a concrete amendment to that schedule's prompt (here: the evening sweep must check in flight-class with dispatch_brief + preflight); until then the distillation is a record of the leak, not a patch on the pipe.
