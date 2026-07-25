---
status: candidate
kind: constraint
date: 2026-07-25
source: "distillation flight sess_5aca9b25 (2026-07-25, scheduled third loop)"
derives_from: "klappy://ars/policy/dispatch-brief-conventions, klappy://canon/values/axioms (Axiom 4)"
queue: "second-brain feeding loop (docs/prd/2026-07-14-second-brain-feeding-loop.md)"
evidence: "run_f8e48966 (2026-07-24T16:24Z): brief said 'Execute the seeded flight oddkit-anon-caps-spec-2026-07-24'; debrief: 'I looked for the source this task points to before writing anything, and I can't find it: no ARS system, seed row…'. Re-dispatch run_fcde461d (16:31Z) carried the full self-contained brief and landed the branch."
---

# A Brief May Not Point at State the Lane Cannot See

**Constraint.** A dispatch brief must be executable from inside the target
lane using only what the brief itself carries plus what that lane can
actually reach. On 2026-07-24 a spec-drafting run was chartered as "execute
the seeded flight <id>" — a pointer into ARS seed state the container
sandbox has no tools to read. The run spent its budget searching for a
source that was, from where it stood, unobservable (Axiom 4), and landed
empty. The immediate re-dispatch with the seed's content inlined landed the
deliverable in seven minutes.

**The distinction.** Pointers are the law for *governance* (fetch, don't
recall) because the lane has oddkit/ars_policy tools to dereference them.
Pointers into dispatcher-side state (seeds, board rows, session logs) are
dead references in a lane without those tools. The test is not "is this a
pointer" but "can the recipient dereference it."

**Proposed rule.** At dispatch, the seat walks every reference in the brief
and asks: can this lane resolve it? If not, inline the content. A brief
that fails the walk does not launch — the cost is one dispatcher minute; the
alternative was a burned flight and a duplicated dispatch.
