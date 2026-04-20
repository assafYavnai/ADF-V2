# ARTIFACTS-README-USES-GLOBAL-FREEZE-RULE

## CONTEXT

Review of the phase-model and foundation support surfaces found that `context/artifacts/README.md` still said artifacts in that folder are not frozen until the CEO explicitly approves them.
That wording was stale against frozen `CONTEXT.md`, which already defines artifact freeze under the global freeze rule and therefore requires approval from both CEO and CTO.

## OPTIONS

- Leave the local artifacts readme with CEO-only wording and let readers infer that `CONTEXT.md` silently overrides it.
- Rewrite the local artifacts readme so it points back to the global freeze rule in `CONTEXT.md`.

## DECISION

The agreed repo-truth rules are:

- `context/artifacts/README.md` must not describe a separate local artifact-freeze rule
- the artifacts readme must stay consistent with frozen `CONTEXT.md`
- artifact freeze is governed by the global freeze rule in `CONTEXT.md`
- artifact freeze therefore requires approval from both CEO and CTO

This decision keeps the local artifacts readme narrow while removing the stale CEO-only wording.

## APPROVAL

EXPLICIT
