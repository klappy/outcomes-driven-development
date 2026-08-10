# Scheduled-lane connector auth flaps — treat loss as transient, and clear the ask on observed recovery

**Seed class:** candidate observation — distilled by the twentieth scheduled distillation fire (sess_b513eb72), 2026-08-09 (fired 2026-08-10T01:04Z).

**Claim:** The ARS connector's auth on the scheduled Cowork lane was lost at the 08-08 ~21:33Z sweep firing (NO-GO recorded), still absent at the 08-09 01:01Z distillation (degraded fire, PR #47), and back by the 08-09 09:34Z sweep — with no captain action visible from any seat. It held again at this fire's boarding (sess_b513eb72 checkin succeeded 2026-08-10T01:03:59Z). This is a flap, not a revocation: a different failure model than PR #47 seed #1's "credentials rot" framing. A charter that finds auth missing should NO-GO or degrade honestly and simply retry next fire; and a standing needs-captain ask filed for an auth loss should be closed by the first flight that observes recovery, or it outlives its truth and pollutes the queue.

## Evidence
- sweep-registry-hygiene-2026-08-08b.md: NO-GO on ARS auth at ~21:33Z 08-08.
- distillation-2026-08-09.md: degraded fire, no checkin possible at 01:01Z; filed needs-captain "re-authorize the ARS connector."
- sweep-registry-hygiene-2026-08-09.md (sess_c99d6861, seq 33118–33119): auth back at 09:34Z, "resolved by observation," no captain action visible.
- This fire: seat-boarded seq 33120, 2026-08-10T01:03:59Z — auth still healthy.

## Proposed canon shape
Observation (scheduled-charter conventions): connector auth on the scheduled lane is flappy — loss is presumptively transient. On loss: probe at preflight, record the honest degraded/NO-GO outcome in the charter's durable-doc fallback ledger, retry next fire; do not escalate as revoked until N consecutive fires fail. On recovery: the observing flight closes the standing auth ask explicitly, citing the observation.
