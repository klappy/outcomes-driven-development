# Text-only deliverables need a text-native validation contract
**Seed class:** candidate — observation, distilled by the scheduled distillation flight, 2026-07-24.
**Claim:** Two frictions in the validation contract surfaced on one flight: (1) `oddkit_validate` demanded artifact classes ("visual proof") that cannot exist for a text-only deliverable, returning NEEDS_ARTIFACTS on an otherwise-clean PASS; (2) the fresh-context validator correctly refused to mint a VERIFIED receipt that names itself as the fresh context — the verdict has to land via the dispatcher — but the checkout gate offers no first-class path for that routing, so the flight parked instead of landing. The gate's letter forced a park on work whose spirit had passed.

## Evidence (window 2026-07-23T01:10Z → 2026-07-24T01:00Z)
- sess_8792378e (charter F3 validation of covenynt/chief-operating-officer PR #3, head 7fe6b478): verdict PASS, 0 blocking findings, empirical checks all green — yet status `parked`, debrief outcome `needs-captain`, validation_verdict null. Its own words: "oddkit_validate returned NEEDS_ARTIFACTS on 'visual proof' only — inapplicable to text-only artifacts; parking rather than minting a VERIFIED receipt referencing myself."
- Downstream cost: sess_b768dde2 had to be flown solely to execute the merge the PASS already justified.

## Proposed mechanism
Validation-mode contract gains an artifact-class declaration (text-only | visual | executable) so NEEDS_ARTIFACTS binds only where the class demands it; and the debrief schema names how a validator-flight's verdict is carried by its dispatcher so a clean PASS can land instead of park.
