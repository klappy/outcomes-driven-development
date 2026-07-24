# PRD — Oddkit Anonymous Caps v1: Meter Rebuilds, Not Requests

**Status:** DRAFT — klappy review required; nothing here is policy until merged.
**Phase:** 0 of 3 in the accounts+billing plan. This PRD covers anonymous caps only. Phases 1–2 (account signup, Stripe billing) are tracked separately and are explicitly out of scope here (§7).
**Prepared:** 2026-07-24, CDO dispatch seat, from the incident brief handed to this seat directly. No `oddkit_time`/`oddkit_orient` telemetry was available in this sandbox, so no flight ID or live canon fetch is claimed — this draft cites only documents read directly from the repo (listed in §8) and evidence given in the dispatch brief. Flagging the gap per Axiom 4 rather than fabricating flight metadata.

> 🎯 One line: oddkit's 2026-07-24 incidents — a 1.5k-request Singapore scanner burst and a knowledge base that rebuilds its index on every single call — trace to one root cause: the worker holds no GitHub credential, so every fetch rides GitHub's ~60/hr anonymous per-IP pool. Fix the credential first (§0), fix the cache-persistence bug second (§1) — capping rebuilds is unfair while the cache that would make them free can't persist — then meter only the units that cost money: index rebuilds and uncached upstream fetches, never cached reads (§2), with per-IP rolling-window caps sized off real telemetry (§3), cached-only degradation instead of hard failure when upstream is tight (§4), and a quota-transparent error contract on every envelope (§5). Recommend a Durable Object counter over KV for enforcement (§6). Accounts, OAuth, and Stripe are explicitly not this PRD (§7).

---

## Summary — Fix the Credential, Fix the Cache, Then Meter the Expensive Thing

Both 2026-07-24 incidents look like separate bugs — a scanner burst and a cache that never hits — but the incident review found one shared cause: oddkit has never carried a GitHub credential. Every upstream fetch, from every deployment, from every IP, has been drawing on GitHub's unauthenticated rate-limit pool, which is shared per-IP at roughly 60 requests/hour. A single burst or a single misconfigured cache key is enough to exhaust it and start returning 403s to everyone behind that IP.

The captain has already added `GITHUB_TOKEN_PUBLIC` (a fine-grained, public-repos-read-only PAT, 5,000/hr) as a secret. Wiring it into the three GitHub fetch paths (`api.github.com`, `codeload.github.com`, `raw.githubusercontent.com`) is Prerequisite A (§0) and lands before any cap does — every number in this PRD assumes the authenticated 5,000/hr budget, not the anonymous 60/hr one it replaces.

Separately, the `github.com/eten-tech-foundation/fluent-platform` knowledge base (scope key `kb_with_required_baseline`) appears to never persist its R2 index — every call looks like a cold-cache rebuild, downloading a 20MB baseline zip plus the user's repo zip from codeload every time. This is Prerequisite B (§1): verify and fix before caps ship, because a rebuild cap punishes a caller for a caching bug that isn't theirs to fix.

With both prerequisites landed, this PRD adds anonymous usage caps that meter the two things that actually cost upstream budget — index rebuilds and uncached fetches — never cached reads, which stay free and unlimited (§2). Caps are per-IP (or per self-identified consumer) on a rolling window, sized from telemetry showing 0–20 misses/hour in normal operation against an abuse signature of 59 misses across 6 requests plus the 1.5k-request burst (§3). When upstream is 403'ing or the quota is tight, oddkit serves the last persisted index with an explicit staleness flag rather than failing outright (§4) — consistent with the repo's anti-cache-lying constraint, which permits staleness as long as it is visible, never silent. Every envelope, not just error ones, carries tier/remaining/window_reset_at so a consumer can see their quota state before they hit it (§5). Enforcement uses a Durable Object counter, not KV, because the cap needs an exact rolling window and KV's eventual consistency would let a burst slip through during propagation lag (§6). Accounts, OAuth, and Stripe billing are not this PRD — they are phases 1–2 of the larger plan and are named here only as the caps' future off-ramp (§7).

---

## §0 — Prerequisite A: Authenticated Fetches

**The bug:** oddkit has no GitHub credential. Every fetch to `api.github.com`, `codeload.github.com`, and `raw.githubusercontent.com` — index builds, baseline downloads, per-repo zips — rides GitHub's unauthenticated rate limit, which is shared per source IP at roughly 60 requests/hour. Cloudflare Workers egress through a small, shared set of IPs, so unrelated traffic (a scanner burst, a cold cache, ordinary daytime usage) can exhaust the same 60/hr pool and produce 403s that look unrelated but share one cause.

**The fix:**

- Attach `Authorization: Bearer ${GITHUB_TOKEN_PUBLIC}` to every request whose host is exactly `api.github.com`, `codeload.github.com`, or `raw.githubusercontent.com`.
- When the `GITHUB_TOKEN_PUBLIC` binding is absent (open-source deployers running their own instance without a token), fall back to unauthenticated requests automatically — no crash, no required configuration to boot the worker.
- The token MUST NOT be attached to, or forwarded toward, any host other than the three named above. A knowledge base's `knowledge_base_url` can in principle point anywhere; the credential is scoped to GitHub's own hosts only, never to a redirect target or a third-party mirror.
- This lifts the shared budget from ~60/hr (anonymous, per-IP, pooled with unrelated traffic) to 5,000/hr (authenticated, dedicated to this token). **Every cap number in §3 assumes the authenticated 5,000/hr world.** If this prerequisite is not live, the caps in §3 are sized for a budget that doesn't exist yet.

This lands first, independent of everything else in this PRD, because it is the fix for the incident itself — the caps in §3 are the longer-term shape, not the immediate mitigation.

## §1 — Prerequisite B: Cache-Persistence Bug

**The observation:** the `eten-tech-foundation/fluent-platform` knowledge base (scope key `kb_with_required_baseline`) shows a 100% miss rate — every call re-downloads the 20MB baseline zip and the user's repo zip from codeload, with no evidence the R2-written index is ever read back on a subsequent call.

**Why this blocks §3:** capping rebuilds is only fair if a well-behaved caller who hits the same scope repeatedly gets a cache hit on the second call. If the write path is silently failing for this scope (or any scope), that caller's every request is a forced rebuild through no fault of their own, and a rolling-window cap turns a caching bug into a hard failure for a real user.

**Before caps enforce, verify:**

1. Does the R2 `PUT` for this scope key complete and return success, or does it fail silently (unawaited write, thrown-and-swallowed error, wrong bucket/binding)?
2. Is the computed cache key stable across calls for this scope — does `kb_with_required_baseline` hash to the same key every time, or does something volatile (a timestamp, an unsorted parameter, a per-request nonce) leak into the key derivation?
3. Does the read path check the key the write path actually used, or has a rename/refactor left the two sides looking at different keys?

This PRD does not prescribe the fix — it names the verification as a hard gate before §3 caps go live for any scope, and flags `kb_with_required_baseline` as the known reproduction case.

## §2 — Metered Units: Rebuilds and Uncached Fetches, Never Cached Reads

The unit this PRD meters is **not** the MCP request. A metered unit is:

- **One index rebuild** — a scope's `BaselineIndex` is not found (or not valid) in R2 for the current commit SHA, and the worker fetches the baseline and/or scope repo from GitHub to build one. A single rebuild may issue more than one upstream GitHub fetch (baseline zip, repo zip); it still counts as one rebuild event against the cap, since that is the unit a caller can observe and a maintainer can reason about.
- **One uncached upstream fetch** — any other GitHub fetch (e.g., a raw file read) that misses the content-addressed cache.

A cached read — any response served entirely from the current SHA-keyed R2 index or content store, per the repo's content-addressed caching design — is **free and unlimited**. This is a deliberate split: the anonymous-caps problem is upstream GitHub budget exhaustion, not MCP traffic volume. A client that reads the same cached knowledge base a thousand times a day costs nothing upstream and should not be capped; a client that forces a thousand rebuilds costs real budget and should be.

## §3 — Per-IP Rolling-Window Caps

**Scope key:** source IP by default. Where a consumer has self-identified (a future API key or account, per phase 1), the cap key becomes the consumer identity instead of the IP — this PRD only specifies the IP-keyed default, since self-identification doesn't exist yet.

**Telemetry basis:**

| Signal | Observed |
|---|---|
| Normal-hours miss rate | 0–20 misses/hour |
| Abuse signature (fluent-platform-style) | 59 misses across 6 requests |
| Scanner burst | ~1.5k requests in one burst |

**Recommendation — two-tier rolling cap per IP:**

- **Hourly cap:** 40 metered units (rebuilds + uncached fetches) per rolling hour. This is 2x the observed normal-hours ceiling (20/hr), giving legitimate bursty use (a first visit to several knowledge bases in one session) real headroom while sitting well below anything resembling the abuse signature.
- **Burst cap:** 15 metered units per rolling 10-minute window. This is the tier that actually catches the observed abuse pattern — 59 misses is not spread evenly across an hour, it is concentrated in a short burst across 6 requests. A pure hourly cap would let that burst complete before the hourly ceiling ever trips; the burst window catches it within minutes.

**Alternatives considered:**

- *Hourly-only cap, no burst tier* — simpler to implement (one counter instead of two), but does not stop the observed abuse shape: 59 misses within an hourly budget of 40 would still trip eventually, but only after most of the damage (and most of the shared 5,000/hr GitHub budget) is already spent. Rejected — the abuse signature is a burst, not a sustained rate, so a purely hourly window catches it too late.
- *Tighter hourly cap (e.g., 20/hr, exactly at the observed normal ceiling)* — maximizes protection but leaves zero headroom for a legitimate user whose normal traffic happens to land at the high end of the observed range; a normal day at 20 misses/hr would immediately trip the cap. Rejected as too tight against real observed normal traffic.

**Residual risk, noted not solved here:** these caps are per-IP. The 5,000/hr authenticated budget (§0) is shared across the whole worker, across all IPs. A coordinated burst from many distinct IPs, each individually under 40/hr, could still exhaust the shared budget in aggregate. A global (worker-wide) ceiling as a second line of defense is worth a future PRD; it is out of scope here because the brief that motivated this PRD is about per-IP fairness, not distributed-abuse defense, and adding it now would conflate two different failure modes in one spec.

## §4 — Cached-Only Degradation Mode

When an upstream GitHub fetch returns 403, or the per-IP quota from §3 is exhausted, oddkit MUST NOT fail the request outright if a persisted index or content object exists for the requested scope. Instead:

- Serve the most recent SHA-keyed index/content from R2.
- Set an explicit staleness flag in the response envelope (e.g., `debug.stale: true` plus a reason, `upstream_403` or `quota_exhausted`), alongside the existing `debug.generated_at` field (`canon/principles/envelope-time-fields.md`) that already carries the content's build time.
- If no persisted index exists at all for the scope (a true cold miss during an outage), the request fails — there is nothing to degrade to.

This is not the TTL-based caching this repo's canon explicitly prohibits (`odd/constraint/anti-cache-lying.md`). The cache is already content-addressed — the key is the commit SHA, not a time window — and this mode changes nothing about when it's written or invalidated. It only changes what oddkit does when a *fresh* fetch is unavailable: serve the *last true* answer, and say so, rather than returning an opaque failure. The constraint's own language is instructive here — staleness is not the violation; silent staleness is. `generated_at` plus the new `stale` flag makes the gap visible instead of hiding it.

## §5 — Limit-Hit Error Contract

Every oddkit envelope — success or error, capped or not — carries quota state, mirroring the two-clock discipline already established for `server_time`/`debug.generated_at`. This PRD did not find an existing "gitauth" quota-transparency doc in this repo to mirror directly (noted as a reading gap in the PR description); the shape below is derived from `canon/principles/envelope-time-fields.md`'s existing precedent of putting observable state on every response rather than only at failure time.

**On every response**, regardless of outcome:

```json
{
  "tier": "anonymous",
  "remaining": 23,
  "limit": 40,
  "window": "1h",
  "window_reset_at": "2026-07-24T19:00:00Z"
}
```

**On a limit-hit response** specifically, the envelope additionally names which limit was hit and where to go next:

```json
{
  "error": "rate_limited",
  "message": "Anonymous hourly rebuild limit reached for this IP.",
  "tier": "anonymous",
  "limit_hit": "hourly",
  "remaining": 0,
  "limit": 40,
  "window": "1h",
  "window_reset_at": "2026-07-24T19:00:00Z",
  "upgrade_path": "Account signup (higher limits) ships in a future phase — not yet available."
}
```

A client can therefore always see its quota state before it runs out, and on a miss, always sees which of the two windows (§3) tripped, exactly when it resets, and an honest statement that a higher-limit path is planned but not yet live — never a dead-end 403.

## §6 — Enforcement Primitive: Durable Object vs KV

**Recommendation: Durable Object counter, one instance per IP (hashed IP as the DO id).**

**Reasoning:**

- KV writes are eventually consistent across Cloudflare's edge (propagation can lag). Two concurrent requests from the same abusive IP, landing on different edge locations within the propagation window, could each read a stale (under-counted) value and both be admitted — exactly the failure mode this PRD exists to close, and structurally the same "confidence without contact with reality" pattern the repo's anti-cache-lying constraint names for content caching, applied here to a counter instead of a document.
- A Durable Object gives a single, strongly-consistent owner for a given IP's counter state. Increment-and-check is atomic within the DO; there is no window where two concurrent requests can both observe "under the limit" when the true post-increment count is over it.
- The two-tier window in §3 (10-minute burst + 1-hour sustained) is naturally expressed as two counters with alarm-based rotation inside one DO instance, rather than two separate KV keys with separate TTL semantics that themselves risk drifting out of sync.

**Cost tradeoff acknowledged:** DOs cost more per-request than a KV read and add a routing hop (worker → DO by IP hash). This is accepted because the thing being protected — the shared 5,000/hr GitHub budget — is exhausted by exactness failures, not by DO latency; an eventually-consistent counter that occasionally over-admits during a burst is precisely the scenario that caused this incident.

## §7 — Non-Goals

This PRD does not cover, and explicitly defers to later phases of the accounts+billing plan:

- **Accounts or account signup.** The error contract in §5 names a future upgrade path; it does not implement one.
- **OAuth or any authentication flow for oddkit consumers.**
- **Stripe or any billing integration.**
- **A global (worker-wide, cross-IP) rate ceiling** — noted as residual risk in §3, deferred to a future PRD.

This search did not locate a "unified-account-launch-plan" document, a "content-addressed-caching implementation" doc at the path canon cross-references (`docs/oddkit/IMPL-content-addressed-caching.md`), or a "gitauth" quota-transparency doc anywhere in this repository — all three are referenced or implied by the dispatch brief and by canon documents this PRD cites, but none exist at a resolvable path in this checkout. This is noted here and in the PR description rather than blocking this draft, per the brief's own instruction.

---

## Definition of Done — Agent/Consumer-Observable Behaviors

Per the Spec DoD Convention (`canon/constraints/definition-of-done.md`), completion is stated as what a consumer can observe, not as an implementation checklist:

1. An anonymous MCP client calling any oddkit tool that only reads cached index/content can make unlimited calls and never receive a rate-limit error.
2. An anonymous MCP client that triggers an index rebuild or uncached upstream fetch can make up to 40 such calls per rolling hour (or 15 per rolling 10 minutes, whichever trips first) from one IP, and can observe `remaining` decrement in every response envelope, not just at failure.
3. An anonymous MCP client that exceeds either window can observe a `rate_limited` error naming which limit was hit, the window, `window_reset_at`, and a stated (not-yet-available) upgrade path — never a bare 403.
4. An anonymous MCP client calling oddkit while upstream GitHub is 403'ing, or while its own quota is exhausted, can observe a successful response built from the last persisted index, carrying `debug.stale: true` and a reason, instead of a hard failure — provided a persisted index exists for that scope.
5. A maintainer re-requesting the `eten-tech-foundation/fluent-platform` scope twice in a row, after the Prerequisite B fix lands, can observe the second call return the same `debug.generated_at` as the first (a cache hit, not a rebuild).
6. A deployer running oddkit with no `GITHUB_TOKEN_PUBLIC` binding can observe the worker serve requests via unauthenticated GitHub calls automatically, with no crash and no configuration required to boot.
7. An operator inspecting outbound requests can observe the `Authorization: Bearer` header present only on requests to `api.github.com`, `codeload.github.com`, and `raw.githubusercontent.com`, and absent on every other host.

## §8 — Rollout

1. Land Prerequisite A (§0) — authenticated fetches. This is the incident fix and should ship independent of everything else.
2. Verify and land Prerequisite B (§1) — cache-persistence fix, confirmed against the `fluent-platform` reproduction case.
3. Implement metering (§2) and the DO-backed rolling caps (§3, §6) behind a flag; dry-run against production traffic to confirm the 40/hr + 15/10min thresholds against real (post-fix) telemetry before enforcing.
4. Add the envelope fields (§5) and cached-only degradation (§4) — these can land alongside the dry run, since they change response shape but not enforcement.
5. Flip enforcement on. Two weeks of measurement against the telemetry in §3 before revisiting the thresholds.

## References Read Before Drafting

- `canon/constraints/definition-of-done.md` — Definition of Done, evidence policy, and the Spec DoD Convention (agent-observable behaviors) applied in this document's DoD section.
- `canon/meta/writing-canon.md` — progressive disclosure checklist this document is structured against.
- `docs/prd/2026-07-14-second-brain-feeding-loop.md` — the only prior PRD in `docs/prd/`; its Status/blockquote/Problem/Decision-cards/Rollout/Non-goals shape is the format convention followed here.
- `odd/constraint/anti-cache-lying.md` — governs the staleness posture in §4; content-addressed caching with a visible staleness flag is compliant, silent staleness is not.
- `canon/principles/envelope-time-fields.md` — precedent for `server_time`/`debug.generated_at` two-clock envelope discipline, extended here to quota fields in §5.
- `canon/principles/knowledge-base-as-the-unit.md` — background on how oddkit's knowledge-base scoping model (referenced in §1's scope-key discussion) works.
- `canon/constraints/oddkit-prompt-pattern.md` — read for context on oddkit conventions generally; not directly load-bearing for this PRD's content.

**Not found in this repository** (searched, not present at any resolvable path): a "unified-account-launch-plan" document, `docs/oddkit/IMPL-content-addressed-caching.md` (referenced by `canon/principles/envelope-time-fields.md`'s own frontmatter but absent from this checkout), and any "gitauth" quota-transparency document. Noted per §7 and in the PR description rather than blocking this draft.
