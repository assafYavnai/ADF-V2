# CONTEXT-GOVERNANCE-CLARIFICATIONS

## CONTEXT

`CONTEXT.md` was reviewed and several contract mismatches were found around artifacts, frozen decisions, current-state authority, rule ownership, commit governance, and handoff refresh behavior.

## OPTIONS

- Leave the draft ambiguous and rely on later interpretation.
- Clarify the governance model now so `CONTEXT.md` can move toward freeze readiness.

## DECISION

The clarified governance model is:
- in-place draft canonical files are allowed
- `context/artifacts/` is for pre-canonical drafts, not for every draft file
- `context/decisions/` holds frozen CEO-approved decisions only
- implicit assumptions are not frozen decisions and should live in handoff or open issues until explicitly approved
- `context/HANDOFF.md` is the primary current-state authority and `context/STATUS.md` is its thin mirror
- if handoff and status ever diverge, handoff wins and status must be aligned immediately
- `RULES.md` is narrow naming and file-convention guidance
- `CONTEXT.md` is the context-governance surface
- every logical repo-truth checkpoint ends with a commit
- handoff must be refreshed after saved decisions and meaningful current-state changes, not only at step completion

## APPROVAL

EXPLICIT
