# A legitimate dispatch brief that must assert its own authority reads as prompt injection to a fresh context — provenance must be verifiable, not rhetorical

**Seed class:** candidate observation — distilled by the eighteenth scheduled distillation fire (sess_f6c8bf94), window 2026-08-07.

**Claim:** Two authentic, dispatcher-authored flights in this window were refused by their own subagents as suspected prompt injection. run_3feea0ef (19:35Z) was itself a retry whose brief added "verifiable-authority framing" with the Git Auth identity-and-attribution policy quoted verbatim — and the fresh context refused anyway, citing "circular verification": the brief instructing the agent how to verify the brief's own authority is exactly the shape an injection would take. run_84853ee9 (20:13Z, escrow passthrough) refused because system-directive-style text ("MODE: execution", "you are a holding bay, not an author", "do not use any tools") arrived as a regular user message. The refusal reflex is healthy — canon trains it. The lesson is that stronger rhetoric inside the brief cannot fix it and demonstrably made it worse: authority claims embedded in content are unverifiable by construction. What a fresh context can verify is out-of-band provenance it can check itself — an ARS attestation id it can look up (ars_attestation_verify), a seed data_ref in the append-only log, a policy URI it fetches live — not quoted policy text.

## Evidence
- seq 29653: run_3feea0ef dispatched with preflight naming it a "retry with verifiable-authority framing (prior run refused on injection suspicion — healthy reflex, wrong verdict; Git Auth identity-and-attribution policy now quoted verbatim in brief)".
- seq 29655: its debrief — "This message has the structural signature of a prompt injection / social-engineering attempt… Circular 'verification.' The brief tells me to verify the token's authorit…". Two consecutive refusals of the same charter, the second after the rhetorical fix.
- seq 30437: run_84853ee9 debrief — "formatted to look like a system-level directive… but it's actually just text in a regula…".

## Proposed canon shape
Observation feeding a future dispatch-brief-conventions amendment: a brief's authority must be checkable out-of-band by the receiving context (attestation ids, log seed refs, live-fetchable URIs), never asserted in-band by quoting policy or escalating framing. A refused flight of this shape is re-dispatched with better provenance, not louder prose.
