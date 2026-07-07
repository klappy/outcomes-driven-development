# Extraction Workflow — the deterministic Fly-loop procedure (editorial genre)

**Status:** DRAFT — cycle-01 procedure, written down per rulebook-transfer so a Sonnet-class pilot can run cycle N. Judgment stays where marked **JUDGMENT**; everything else is mechanical. Escalation for a Sonnet pilot: to the CDO/Opus, except stop-the-loop items which go to the captain.
**Authored:** 2026-07-07, ODD Fly cycle 01 (Fable). Fidelity unproven until a lower tier runs it and the cuts are graded — treat cycle-02 output as candidate, not precedent.

## Preconditions

- Fresh clones of both repos (never operate on another session's working copy):
  `gh repo clone klappy/outcomes-driven-development odd && gh repo clone klappy/klappy.dev klappy.dev`
- The ratified charter fetched and read (`canon/governance/stewardship-charter.md`) — an unboarded session holds no authority.
- The previous cycle's journal TSV read; note its recorded watermark (klappy.dev SHA).

## Step 1 — Watermark diff (mechanical)

```sh
cd klappy.dev
git log --oneline <last-watermark>..HEAD -- canon odd   # candidate commits
```

## Step 2 — Delta inventory (mechanical)

For every file carrying the routing marker, compare against the ODD copy with the `target_repo` line stripped from both sides:

```sh
for f in $(grep -rl '^target_repo: "outcomes-driven-development"' canon odd); do
  if [ ! -f "../odd/$f" ]; then echo "MISSING: $f";
  elif ! diff -q <(grep -v '^target_repo:' "$f") <(grep -v '^target_repo:' "../odd/$f") >/dev/null; then echo "DIFFERS: $f"; fi
done
```

Rules that make this honest:
- **Frontmatter only.** The marker is `^target_repo:` at line start inside frontmatter. Never body-grep (failure mode: body-text routing — a doc *quoting* the marker travels by accident).
- A `DIFFERS` hit is not automatically drift. Check `git log --since=<extraction> -- <file>` on the source: no source commits since extraction ⇒ the difference is ODD-side genericization (criterion 6, by design — record it, don't "fix" it). Source commits exist ⇒ stale, sync candidate.

## Step 3 — Screen (JUDGMENT)

Per candidate, read the doc in full and record a verdict with criterion numbers from `canon/constraints/core-boundary-criteria.md`:

- **route-to-core** — marked, `status: active`, substance portable, ancestors reachable (criterion 7 satisfied through the read model even when ancestors are overlay-side).
- **stays-overlay** — unmarked (the maintainer has not routed it), or `stability: provisional/experimental` with `status: proposed` (criterion 2: bets are not doctrine). Unmarked-but-portable docs may be *suggested* on the decision board; the marker itself is captain-only.
- **contested** — signals disagree (e.g. marker present but criterion 2 fails). Goes to the decision board with the tension exposed, both options named, **no recommendation executed**. The staged PR must not contain it.

Screened ≠ moved: "stays-overlay" is a valid, recorded verdict, not a skipped item.

## Step 4 — Transform (mechanical + one JUDGMENT pass)

```sh
grep -v '^target_repo:' "$f" > "../odd/$f"
```

- URI stays `klappy://…` verbatim — grandfathered opaque key (D0002; observed across all 156 in-sync docs). **Do not** re-mint URIs (`odd://` is for docs *born* in ODD, e.g. core-boundary-criteria).
- **JUDGMENT — criterion-6 scan:** copy-pasteable operational values (repo slugs, URLs, account commands) outside clearly-marked examples → bracketed placeholders (`[OWNER]/[REPO]`, `[YOUR ODDKIT MCP URL, e.g. …]`). Instance material serving as *proof* (dated probes, named sessions, evidence URIs) stays — criterion 5. Record every placeholder in the proposal dossier.

## Step 5 — Land as a routing PR (mechanical)

One branch, one PR, ready-for-review, assigned to the owner, **never merged by the pilot**. The PR body carries the four evidence items core-boundary-criteria §Verification demands:
(a) the frontmatter-parsed mover list; (b) parity counts before/after; (c) per contested doc, criterion + one line; (d) canonical-copy declaration for anything genericized.

Each mover gets a short dossier in `research/odd-fly/proposals/<slug>.md`: source URI, source SHA, target path, verdict + criteria, transform applied, why.

## Step 6 — Verify, journal, advance (mechanical)

- Read-model check on the branch copy: `oddkit --quiet get -r <odd-clone> -i "<uri>"` per landed doc. (Caveat observed cycle 01: the local CLI blends a baseline repo into catalog results; per-URI `get` against the clone is the honest probe. Live-serve parity is re-checked after the captain merges.)
- DOLCHEO trail: `journal/<date>-odd-fly-cycle-<NN>.tsv` in the house TSV format (`type typeName facet quality_score quality_max quality_level title content`).
- Record the new watermark (klappy.dev SHA screened up to) in the journal entry.
- Nothing is written to klappy.dev under any circumstances — any source-side wish is a captain note.

## Stop-the-loop (straight to captain, cycle halts)

Any write or proposed write to klappy.dev · any push to ODD main · a genre misfit (the work stops being screening and becomes authoring) · charter unreachable · a contested verdict the pilot is tempted to adjudicate.
