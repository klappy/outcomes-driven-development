# A blocked debrief carries its executable fallback
**Seed class:** candidate (principle) — distilled by the scheduled distillation debrief, 2026-07-31 fire (sess_7c04c181).
**Claim:** A debrief that declares `blocked` should name the concrete, executable alternative in the same breath as the block — because a block that carries its fallback is half-recovered before anyone reads it. The expectation isn't merely "I stopped and said so"; it is "I stopped, said so, and left the next crew a runnable move."

## Evidence (paid for in-window, 2026-07-30)
- run_4a923ffa (API-lane smoke): blocked at 13:45:54Z — ANTHROPIC_API_KEY not provisioned. The machine-drafted debrief did two things right: it refused silent fallback, and it named the exact alternative ("pass `needs_fs: true` to use the container lane meanwhile") plus the captain-owed fix (worker secret). Log seq 17747–17749.
- run_347d8a4f: the seat executed that named alternative within the same minute-window (dispatched 13:45:54Z, finished ok 13:46:52Z) and landed PASS. Log seq 17946–17950. Block → recovery in under an hour, zero captain round-trips consumed for the recovery itself (the credential ask is the only thing escalated, correctly, as the captain-owned half).

## Contrast class
The 07-28 sweep dark day (undiagnosed miss, PR #36/#37 lineage): a gap with no debrief and no named next move required two subsequent flights just to characterize it — and its cause is still unknown. The delta between these two failure handlings is exactly the presence of a named fallback at block time.

## Proposed norm
Add to the debrief contract for `blocked` outcomes: the summary MUST carry (a) the blocking fact, (b) the owner of the fix (seat vs captain, tagged), and (c) one executable alternative or an explicit "no alternative exists." A blocked debrief without a fallback line is an incomplete debrief.
