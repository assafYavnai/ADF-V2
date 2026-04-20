# CONTEXT-ARTIFACT-FREEZE-WORDING-USES-GLOBAL-RULE

## CONTEXT

A deeper carry-through audit found that frozen `CONTEXT.md` still used one older CEO-only sentence in the artifact freeze section even though the repo had already agreed that artifact freeze follows the global freeze rule and therefore requires approval from both CEO and CTO.
The same section also said rejected freeze attempts should apply `CEO comments`, which kept the same stale actor-specific phrasing alive inside the bootstrap truth surface.

## OPTIONS

- Leave the mixed wording in `CONTEXT.md` and rely on readers to reconcile the later global-rule sentence by inference.
- Normalize the artifact-freeze request and rejection wording in `CONTEXT.md` so the whole section uses the already agreed global freeze rule consistently.

## DECISION

The agreed repo-truth rules are:

- `CONTEXT.md` must describe artifact freeze requests in terms of the global freeze rule, not as a CEO-only approval request
- `CONTEXT.md` must describe freeze rejection handling in actor-neutral wording that matches the same global approval model
- this clarification does not create a new freeze rule; it only removes stale wording so the existing global CEO+CTO rule is expressed consistently inside the bootstrap truth surface

## APPROVAL

EXPLICIT
