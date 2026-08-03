# An interactive seat that does not log its turns is a dark flight in the registry

**Seed class:** candidate observation — distilled by the thirteenth scheduled distillation fire, 2026-08-03.

**Claim:** Interactive seat sess_6641796b flew ~15 hours (boarded 2026-08-02T00:48Z) with zero heartbeats while doing some of the most consequential work of the window — the Own-Brain Grant charter merged (cdo#145 @ d0fa2c0), 13 ODD seed PRs merged under seat authority, 17 seat-authority merges total. The registry showed a silent seat; the work was invisible to every tower sweep in between. The captain caught it, and the fix was legislated live the same session: per-turn seat logging (cdo policy 22 v1.1.0, encoded by flight A4 as cdo#147, fresh-context ratified and merged by flight V5 @ 975ee9c), with the backfill heartbeat itself the first exhibit.

## Evidence
- seq 19729–19730: mode-declared + backfill heartbeat, verbatim: "BACKFILL TURN LOG (seat flew ~15h with zero heartbeats — captain called it; live exhibit for the per-turn logging rule)."
- seq 19731: first compliant turn log, citing policy(22) v1.1.0 and its merge trail (cdo#147, 975ee9c).
- Contrast: dispatched flights the same window (sess_2e4928fb, sess_1b109aaa, sess_08275d94) were fully legible — seeded, leased, debriefed, VERIFIED.

## Proposed canon shape
Observation for ODD canon (the rule itself already lives in cdo policy 22): the recorder/validation gates make dispatched flights legible, but an interactive seat is exempt from all of them, so the seats doing the highest-authority work are the least observable. Legibility must not depend on lifecycle class — a seat that exercises merge authority owes the log a turn-by-turn trail the same way a flight owes a debrief.
