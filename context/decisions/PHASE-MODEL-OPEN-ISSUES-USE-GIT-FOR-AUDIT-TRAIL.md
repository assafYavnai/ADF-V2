# PHASE-MODEL-OPEN-ISSUES-USE-GIT-FOR-AUDIT-TRAIL

## CONTEXT

During review of the target phase model, a question came up about whether an empty `OPEN-ISSUES.md` provides enough auditability to understand what the implementing agent actually did.
One option was to add another local audit file such as `ACTIVITY.md`.
The counterpoint was that the model already has a file surface plus git, and future context architecture may move away from markdown entirely, so adding another permanent history layer now would create unnecessary mechanism.

## OPTIONS

- Add a separate append-only activity ledger such as `ACTIVITY.md` for each step.
- Keep `OPEN-ISSUES.md` as a current-state file and rely on git history without any additional rule.
- Keep `OPEN-ISSUES.md` as a current-state file and add an explicit commit rule so git becomes the governed audit trail for open-issue lifecycle changes.

## DECISION

The agreed target phase-model rules are:

- `OPEN-ISSUES.md` remains a current-state surface, not a narrative history ledger
- audit trail for open-issue creation, closure, transfer, and final-clear state is provided by git checkpoints tied to the related repo-truth change
- an empty `OPEN-ISSUES.md` means only that no issues are currently open at that scope
- an empty `OPEN-ISSUES.md` does not itself distinguish whether no issue was ever found, all issues were resolved locally, or issues were transferred upward
- every meaningful `OPEN-ISSUES.md` update must be committed in the same logical checkpoint as the event it records
- do not leave open-issue lifecycle changes uncommitted across later unrelated work
- `OPEN-ISSUES.md` does not require a separate dedicated commit when the related repo-truth change is already part of the same logical checkpoint
- each open issue entry must follow the lean file-friendly open issue entry contract defined in the phase-model artifact
- open issue entries do not use issue IDs at this stage; the title is the human handle
- each entry must preserve one unresolved reality gap and include concrete evidence, impact, next action, closure condition, last meaningful update, and source session when available
- `Owner` may be an owning scope or responsible actor, not necessarily a person

This decision keeps the model simple, uses git as the audit layer, and avoids introducing a second local history surface that the future context architecture may not keep.

## APPROVAL

EXPLICIT
