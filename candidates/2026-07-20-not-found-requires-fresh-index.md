# Candidate: NOT_FOUND requires a fresh index — a search miss is not evidence of absence

**Claim.** When a canon search misses a term the human clearly expects to
exist, the agent must verify index freshness (served index sha vs. repo main)
before concluding absence. Until verified, the honest report is "my index may
be behind," never "nothing surfaces under that name." Corollary hazard: an
agent that gracefully synthesizes over a stale miss can fork a term canon
already owns — inventing a parallel meaning for a name that has a ratified
one.

**Evidence (two independent incidents, same day, different sessions).**
1. 2026-07-20 ~13:00Z — dispatch seat resolved
   `klappy://canon/meta/policies-vs-requirements` immediately after its merge:
   NOT_FOUND; served index pinned to a pre-merge sha. Named at the time as
   seed-5's pattern ("a cache is a lie in wait") and disclosed rather than
   promised away.
2. 2026-07-20, separate session — a second agent searched "third loop" for
   the just-landed `klappy://canon/methods/triple-loop-debrief-review`,
   reported "nothing surfaces," and improvised an adjacent three-layer
   framing — a coherent but *different* concept than the ratified one. The
   captain caught the miss; P0012's own failure-mode line ("the class of
   catch does not scale past the attention of whoever is watching") predicted
   it verbatim.

**Mechanism owed (over promise).** oddkit should disclose index sha + age in
every search/resolve response (agents can then *see* staleness), and/or bust
the index cache on merge. Until then this is agent discipline: on an
unexpected miss, check `oddkit_version` / index sha against repo main.

**Status.** Single-day evidence but two sessions and a consequence
(concept-fork risk); related to but distinct from the held cache-honesty seed.
