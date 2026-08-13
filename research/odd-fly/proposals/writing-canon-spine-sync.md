# Proposal — Writing Canon spine sync (stale-copy repair)

| Field | Value |
|---|---|
| Source | `klappy://canon/meta/writing-canon` — `klappy/klappy.dev` @ `1a4919c` (#265: the reader's one-line demand — "Show me what I'm deciding in a way that respects my attention and time" — added as the document's spine; 2 lines changed) |
| Target | `canon/meta/writing-canon.md` (sync staged); URI unchanged |
| Verdict | **stale-copy repair** — the doc was routed core at the bifurcation (#237) and both copies were in sync until #265 landed source-side |
| Criteria | Already-adjudicated core doc; the delta is voice-neutral and instance-free, so the original routing verdict stands unchanged |
| Transform | Verbatim minus `target_repo` |
| Ratification | Captain's merge only. Original untouched |

**Why.** The writing canon governs every document in this repo (extraction-depth discipline); serving the pre-#265 text means adopters get the rule without its stated spine. Two-line drift is exactly the class of divergence the weekly watermark loop exists to catch while it is still trivial.
