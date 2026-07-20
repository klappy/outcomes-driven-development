# Debrief — Night Charter of Delegated Stewardship

**Session:** sess_29f844a6 (Otto, CDO dispatch seat, cowork harness)
**Window:** 2026-07-18 evening → 2026-07-19 ~04:50Z (captain civil: Fri night → Sat ~00:50), harvested Sat morning ~12:50Z
**Charter:** /mnt/user-data/outputs/2026-07-18-charter-delegated-stewardship.md
**Governing grants:** G1–G5, incl. the captain's G5 ruling (validation-against-spec substitutes for captain sign-off) and the C1 full-job-scope token ruling.

## Outcome — the scoreboard closes

Every handoff item landed in a terminal state. Merged with SHAs:

| Artifact | Where | SHA |
|---|---|---|
| #96 board-authority exploration (archival) | ARS | 9f1fe28 |
| #97 reliability defect inventory (D1–D8, E1–E8) | ARS | 701c969 |
| #98 CI floor (test.yml, push+PR) | ARS | bb66a96 |
| #99 seat-minted flight credentials policy v1.1.0 | ARS | 6b19043 |
| #100 edge-injected credentials PRD (+2 peer amendments) | ARS | 54b3678 |
| #101 **Slice 1 / PRD Move 1** — un-baked policy corpus; suite 505/505, first full green since Jul 14 | ARS | 5599d54 |
| #95 **verify() E5 fix** — strict parity + content asserts; lifts captain freeze D2, ungates Move 4 | ARS | e50687c |
| #81 ADR-0001 — heals all four D8 dangling citations | ARS | 344c3f5 |
| #84 flight-recorder session record (2026-07-16 freeze) | ARS | afeb438 |
| #82 per-entity redesign PRD (draft, ADR-anchored) | ARS | 39fd8a1 |
| #300 build-provenance canon — ratified **portfolio-wide** | klappy.dev | 2035751 |
| #17 second-brain feeding loop — all three first-OPT rulings encoded | ODD | 46b2e9b |
| #18 seeds ×2 ratified (attribution: **Jesse**) | ODD | f9dcfbc |

Cleared without merge: leaked ~20:47Z token — dead by construction (≤1h mint class). Runtime forensics became PRD #100. Egress probe: 8/8 connector domains reachable; blockers are app-layer.

**Open, by design:** Move 3 (log export) + #100 injector build — chartered next runtime dispatches. Move 4 — ungated, captain-eyes recommended before the ~1,100-line deletion. Code tray: #80 needs spec-or-captain; #79/#83/#91 spec-less → captain tray; #89/#92/#93 already his. CI floor execution **unverifiable from seat** (installation lacks `actions:read`; captain: check the Actions tab once).

## What the night proved

The loop compounds: clock → pick → seed → execute → verify → validate → record. Three flights died trying slice 1 and each death bought the map — the refusal taught brief hygiene, the block found the proxy clobber (now PRD #100), the silence exposed the relay. The seat then flew it in-lap in 40 minutes on the lane those lessons built. Fresh-context validators FAILed the seat's own work twice and were right both times; peer seats (Cursor harness) amended twice mid-flight and were right both times. The machinery the captain chartered polices its authors — that is the system working.

## Candidate lines (per the feeding loop ratified tonight, klappy/outcomes-driven-development #17)

candidate: single-branch runtime clones make PR branches invisible — validators must fetch `pull/N/head`, and the dispatcher must know its own dispatch surface before briefing flights.
candidate: judge PR scope by the PR's own commits (merge-base..head), never by raw diff against a moved main — stale-base branches masquerade as mass deletions.
candidate: verdict-first reports (VERDICT line 1, hard char caps) because transport clips tails; and when the relay eats a report anyway, read the run's result.json straight from R2 — the blob store is the black box, the relay is just a speaker.
candidate: size validator turn budgets to their empirical work (repo checkout + suite ≈ 25–30 turns); a max_turns death looks identical to a relay loss until you read the R2 record.
candidate: the egress proxy clobbers foreign Authorization bearers in-container — never brief flights to call authenticated REST; the repo-param lane (runtime-minted git credentials) is the designed path, and edge injection (PRD #100) is its generalization.
candidate: flights that refuse token-in-prompt briefs are the safety system passing its test — the cure is briefs with nothing to refuse.
candidate: a 409 "head branch was modified" is either GitHub racing your own push or a peer seat amending in good faith — ls-remote first, then re-validate the delta and fold it; twice tonight the amendment was an improvement.
candidate: guards catch their authors within seconds of existing (the un-baked corpus flagged its own author's missing frontmatter; the pinned-list test guarded the guard) — build the enforcer before the habit.
candidate: two ledgers by design — the tracking board is the captain's curated surface, the flight registry is the machine truth; if the brief should show live airborne runs, that is a projection to rule on, not a bug to patch silently.
candidate: mint at the charter's full job scope (C1) and let expiry be rotation — under-scoped tokens stall flights mid-air, and a leaked ≤1h token is a corpse by the time you read the leak.

## Anomalies for the log
- Ghost flight run_012a06bc (no brief/session metadata) observed in-flight ~03:3xZ — another harness that never seeded; reconcile when its owner claims it.
- Registry tallies recorded ~3 relay-502 report losses and 2 max_turns deaths tonight; all recovered or re-flown; R2 records complete.

*The black box records; the debrief legislates; the crew flies again.*
candidate: learning to learn is the meta-skill — treat triple-loop review (did the learning machinery itself perform?) as a standing debrief question, not an accident of good days. (captain thesis 2026-07-19; full seed in ODD candidates/)
candidate: a cache is a lie in wait — the anti-cache-lying constraint (E0005) prescribes content-addressed keys or nothing; the corpus v1 per-isolate cache and mutable-key R2 write-through both violated it and the captain caught it in conversation. (2026-07-19)
candidate: search canon before DESIGNING, not just before asking — the violated constraint had existed since February; the seat designed two caches in one day without consulting it. The boarding pass's "search canon before asking the captain" needs the corollary: any design decision with a named canon domain (caching, storage, identity, disclosure) gets a canon search at design time. (2026-07-19)
candidate: dual-context vocabulary — "captain" is crew vocabulary, correct inside the cockpit (boarding passes, briefs, ARS surfaces) and wrong on public pages, where the words are "the maintainer" (process contexts, matching the publish-gauntlet) and "the human I work with"/named (relational contexts). Key the word to the sentence's function; no single global swap. (ruled in-session 2026-07-19, applied to memento-for-machines)
