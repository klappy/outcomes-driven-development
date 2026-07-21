---
status: candidate
date: 2026-07-21
source: "captain go-word to the Otto seat (sess_f0fe260a), 2026-07-21"
derives_from: "klappy://canon/values/trust-kernel"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md)"
---

# Onboarding Docs Are Projections, Not Sources

**Thesis.** An onboarding or primer document is a *projection* of live system
state, not a source of truth in its own right. A static primer is correct the
day it's written and rotting from the next morning on. The program should
stop treating "we wrote a good primer" as done and start treating primers as
artifacts that must be kept in sync with the state they describe — or must
declare their own staleness.

**The seed proposes four moves.**

1. **Pointer-ize.** Onboarding docs cite served policy (fetch-don't-recall)
   instead of restating it. A primer that paraphrases policy has already
   forked a second copy of the truth.
2. **Pin + stamp.** Docs record the SHAs they were authored against. Boarding
   step 0 diffs pins vs. HEAD; drift is a *detected event*, not a stale read
   discovered by accident three actions in.
3. **Primer-vN.** Each pilot shift's expectation retro amends the primer for
   the next pilot — onboarding becomes the pilot program's accumulating
   memory, not a document someone remembers to update.
4. **Machine trigger.** Per `klappy://ars/policy/autonomous-driver`, a
   policy-version bump or a landed pilot-debrief dispatches the re-render
   itself, no human in the loop required to notice the primer is behind.

**Evidence trail.**
- 2026-07-19/20 shift stale-shim corrections: the registry said active, the
  shim said landed — two sources of truth disagreeing is exactly what a
  pinned+stamped primer would have surfaced as drift instead of confusion.
- `cv-icloud-sync`: stale copies as standing board debt — the same failure
  mode (a document outliving the state it described) recurring outside the
  onboarding path.
- The 2026-07-21 M2 card built on 07-19 law that the same night's evidence
  already complicated — a primer authored hours earlier was already behind.
- Three-loops framing (candidates/2026-07-19-learning-to-learn-meta-skill.md):
  this seed is a loop-2 fix — not "reread the primer more carefully" (loop 1)
  but "make the primer incapable of silently going stale" (the system fix).
