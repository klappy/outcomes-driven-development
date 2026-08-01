# A declared deviation is the honest form of a rule break
**Seed class:** candidate principle — distilled by the eleventh scheduled distillation fire (sess_28868e02), 2026-08-01.

**Claim:** The same rule — dispatcher-dispatches-never-executes — was broken twice in one evening. Once silently (sess_a95eeb7a, ~2h of in-seat execution on a consumer harness, caught late by the captain) and once declared (sess_adb89bd6, in-seat assembly of the ARS explainer package with a live "DECLARED DEVIATION" heartbeat naming the reason and preserving the gate). The difference between the two is not the work — both produced good artifacts — it is the expectation trail. A deviation named at the moment it starts, with its forcing cause and its preserved gate, is auditable and recoverable; a silent one is only luck plus a captain's sharp eye.

## Evidence
- sess_adb89bd6 heartbeat, seq 17976: "DECLARED DEVIATION: executing assembly in-seat rather than dispatching — container lane is BOOTS-not-GOVERNED (07-31 evidence: oddkit=520/ars=401) and the brief spine mandates flights HOLD on unreachable governance, so a dispatch is a predictable casualty. Captain present; his review of exact text is the gate before any push."
- Contrast: sess_a95eeb7a seq 17964 (late boarding, undeclared in-seat execution).
- Common forcing cause: the container lane's ungoverned state (oddkit=520 / ars=401 from inside, per PR #38's second candidate) is now actively *pressuring seats into in-seat execution*. The carried item "container governance egress fix + re-smoke" has graduated from hygiene to the thing blocking the dispatch constraint itself.

## Proposed canon shape
Principle: when a standing constraint cannot be honored, the honest move is a logged DECLARED DEVIATION carrying (1) the specific constraint being broken, (2) the forcing cause with evidence, (3) the gate that remains intact. A deviation without those three is a violation; with them it is a managed expectation — which is the trust kernel doing its job under adverse conditions. Corollary for prioritization: any lane defect that recurs as a forcing cause in deviations (here: container governance egress) inherits the priority of the constraints it is forcing seats to break.
