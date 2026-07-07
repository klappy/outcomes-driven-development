# Proposal — DOLCHEOT: Tension encoding type + vocabulary sync (route-to-core, drift repair)

One proposal, two files — they shipped as one source change (#261) and are meaningless apart.

| Field | Value |
|---|---|
| Source | `klappy://odd/encoding-types/tension` (new) + `klappy://canon/definitions/dolcheo-vocabulary` (updated DOLCHEO→DOLCHEOT, seven→eight, E0008.3→E0009) — `klappy/klappy.dev` @ `1a4919c` (#261) |
| Target | `odd/encoding-types/tension.md` (new) + `canon/definitions/dolcheo-vocabulary.md` (sync) — both staged; URIs unchanged |
| Verdict | **route-to-core** — for tension.md, and **stale-copy repair** for the vocabulary |
| Criteria | Both marked. Precedent decides tension.md's home: all seven sibling encoding-type docs plus `serialization-format.md` already live in this repo's `odd/encoding-types/` — an eighth letter defined anywhere else is stranded derivation (criterion 7). Its `governs: oddkit_encode parsing` does not make it an oddkit manual (criterion 4): the encoding types are ODD's vocabulary that the tool *enforces*, same as the seven already here. Additive: a DOLCHEO journal with zero Tensions stays valid |
| Transform | Verbatim minus `target_repo`, both files. No genericization needed |
| Ratification | Captain's merge only. Originals untouched |

**Why this is also an incident, not just a sync.** This repo's README declares it "the write model for the `odd://` authority — authoring happens here via PRs." #261 was authored in klappy.dev on 2026-06-24 and never reached this repo: for two weeks the read model has served a seven-letter DOLCHEO while the source of record teaches eight. That is the **double-homing** failure mode core-boundary-criteria names ("redundant state invites drift"), observed live. The sync staged here repairs the drift; the *authoring-home question it exposes* (which repo is where core-routed docs are born?) is a decision-board item for the captain, deliberately not adjudicated here.
