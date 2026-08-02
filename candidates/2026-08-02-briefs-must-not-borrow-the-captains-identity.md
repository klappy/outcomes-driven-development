# A brief that asks a flight to wear the captain's git identity will be refused — attribute as the seat, not the human

**Seed class:** candidate constraint — distilled by the twelfth scheduled distillation fire (sess_8b89b5e8), 2026-08-02.

**Claim:** Two container dispatches in one evening were refused by their own flight models because the brief's setup step instructed `git config user.name / user.email` set to the captain's personal identity. The refusals were correct: impersonating a human in commit metadata is an integrity violation from the flight's side, whatever the dispatcher intended. The cost was two spent dispatches and ~10 minutes of lane time before the seat rewrote the brief; the fix was already law at the token layer — Git_Repo_Auth's attribution guidance mandates the operator's `{id}+{login}@users.noreply.github.com` no-reply identity — but that law had never been copied down into the dispatch-brief conventions, so briefs kept re-inventing attribution and got it wrong.

## Evidence
- run_66358c72 (seq 19022, 2026-08-01T03:55Z): "I'm not going to run this as scripted… The setup step asks me to run `git config user.name/user.email`. That's an explicit 'never do this' in my own operating rules — I don't change git identity config, and I especially won't set it to impersonate a…"
- run_916bbb02 (seq 19234, 2026-08-01T03:58Z): flagged the brief for "pre-arguing that setting the git commit author/committer to a specific human's name and personal GitHub…" before doing any work.
- Both dispatched from sess_f87f0300 (NotebookLM video package flight, landed VERIFIED at 04:09Z) — the mission succeeded only after the briefs stopped asking for the identity.

## Proposed canon shape
Constraint (dispatch-brief-conventions amendment): a dispatch brief MUST specify commit attribution as the seat's no-reply app identity (per klappy://ars/policy/seat-minted-flight-credentials and Git_Repo_Auth attribution docs) and MUST NOT instruct a flight to set git identity to any human's name or email. A refusal on these grounds is a correct outcome, not a malfunction — but a brief that provokes it is a dispatcher defect. Corollary: when a law exists at one layer (token custody) and briefs at another layer keep violating it, the law is under-propagated — copy the pointer into the conventions the brief-writer actually reads.
