# Bounded charters fly clean on the lane that kills open-ended ones — bound the charter, not the lane

**Seed class:** candidate observation — distilled by the sixteenth scheduled distillation fire (sess_cc610493), 2026-08-05 (captain civil date; UTC 2026-08-06T01:02Z).

**Claim:** The container lane's July record was five consecutive casualties on the distillation charter (runs fb133d81, 8bf49be4, 7efeae98, 9177ea77, 97e78310 — run-lost or sandbox failure), which produced the standing lane note "do the work in-session, never dispatch container runs for this." On 2026-08-05 the same lane flew nine runs in one day for one dispatcher (sess_78b50062) with zero losses: seed → retrieval ×3 → validation → iteration → correction → retrieval ×2, every one finished done/ok in 16–86 seconds (seq 22616 through 24468). The variable that changed is not the lane — it is the charter. The July casualties were long, open-ended, multi-step charters (a full distillation: read registry, audit, write, push, PR). The August successes were single-purpose, bounded, minutes-long tasks with one required output each. The lesson generalizes the existing mode-discipline law with an empirical reliability claim: charter length is the dominant survival factor on the container lane, so the response to lane casualties is decomposition, not lane abandonment.

## Evidence
- July casualty set: five distillation-charter container runs lost 2026-07-20/21 (recorded in the distillation charter's own lane note and prior debriefs; the charter now flies scheduled-session lane).
- August success set: run_ad290ff1 (seed), run_2e2/… retrievals run_2a9a96e9 / run_89b6896e / run_5e390565, validation run_70567c39 (VERIFIED-WITH-FINDINGS), iteration run_a2713ed8, correction run_4b7cc642 (v3, sha256-addressed), run_d4071a3e, run_8077cd4e, run_76142054 — all done/ok, longest wall-clock 86s (seq 23302→23303), shortest 16s (seq 24467→24468).
- Same account, same lane, same month-scale infrastructure; the only systematic difference observed is charter scope.

## Proposed canon shape
Observation feeding a principle: when a lane shows casualties, first ask whether the charter fits the lane's endurance before writing the lane off. Container-lane dispatch guidance: decompose to single-output tasks measured in minutes; keep anything requiring sustained multi-step context on a session lane. (Caveat kept honest: nine bounded successes and five open-ended failures is correlation across different workloads, not a controlled proof — the seed proposes guidance, not law.)
