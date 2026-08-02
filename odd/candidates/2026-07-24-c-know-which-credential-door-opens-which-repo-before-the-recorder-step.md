# Know which credential door opens which repo before the recorder step
**Seed class:** candidate — observation, distilled by the scheduled distillation flight, 2026-07-24.
**Claim:** The account now has two GitHub App installations (klappy/* via Git_Repo_Auth, covenynt/* via Git_Covenynt). A token from the wrong door returns "Repository not found" — indistinguishable from a missing repo — and a flight that discovers this at its RECORDER step has already done the work and can no longer file it where the pointer norm expects. Credential-to-repo mapping is boarding-time verification, not landing-time discovery.

## Evidence (window 2026-07-23T01:10Z → 2026-07-24T01:00Z)
- sess_98535d36 (tower sweep, 2026-07-23T21:33–21:40Z): completed a full registry-hygiene sweep, then could not push its report to klappy/chief-delegation-officer — "clone → 'Repository not found' even with a repo-scoped write token; Covenynt installation is a different account." Filed as a project doc with an explicit needs-captain note that the no-pointer-means-dark norm hangs on the captain accepting the substitute. (claude/sweep-registry-hygiene-2026-07-23.md)
- Same sweep: personal-cashflow survivor checks (sess_5d556a78 / sess_ad55163c) impossible for the same reason — repo outside the grant.
- Contrast: this distillation flight verified its write door (relay GET /api/users/klappy → 118073) at boarding, per the standing lane note, and filed normally.

## Proposed mechanism
Any charter whose brief names target repos lists them against the credential door that opens them; boarding preflight includes one cheap authenticated read per named repo. A "Repository not found" on a repo the registry says exists is a grant problem until proven otherwise.
