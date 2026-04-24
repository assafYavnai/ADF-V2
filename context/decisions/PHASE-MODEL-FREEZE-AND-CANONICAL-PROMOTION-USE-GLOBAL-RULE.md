# PHASE-MODEL-FREEZE-AND-CANONICAL-PROMOTION-USE-GLOBAL-RULE

## CONTEXT

The seven-finding review found that the target phase model still used weaker approval wording than the frozen global freeze rule.
The phase model said freeze gate and close gate require explicit user approval, while frozen governance already says any freeze, including step freeze, phase freeze, and artifact freeze for promotion, requires approval from both CEO and CTO.

The same finding also noticed that phase promotion can move collected artifacts from phase-local `artifacts/` into canonical repo locations.
That movement changes trusted repo truth and must not bypass artifact-freeze approval.

## PUSHBACK

The pushback was:
- freeze gate approval could be interpreted as generic user approval instead of CEO+CTO approval under the global freeze rule
- phase close approval plus mechanical promotion could move artifacts into canonical repo truth without recording artifact-freeze approval
- the model needed to preserve mechanical promotion after approval without weakening the approval actor rules

## DISCUSSION SUMMARY

The approved resolution separates approval actors by transition.
Freeze gates are freeze events, so they require CEO+CTO approval under the global freeze rule.
Close gates remain explicit user approvals unless the close approval also authorizes canonical artifact promotion.

Step promotion from step `drafts/` to phase `artifacts/` remains mechanical after step close because those artifacts are still isolated inside the active phase.
Phase promotion can also remain mechanical after close, but canonical artifact movement may happen only after CEO+CTO artifact-freeze approval is recorded.
That approval may be recorded as part of the phase close gate or as a prior explicit artifact-freeze approval.

## OPTIONS

- Keep generic explicit user approval for freeze gates.
- Make promotion a separate approval gate.
- Bind freeze gates and canonical artifact promotion to the global CEO+CTO freeze rule while keeping promotion mechanical after the required approval is recorded.

## DECISION

The agreed target phase-model rules are:

- freeze gate approval requires CEO+CTO approval under the global freeze rule
- close gate approval requires explicit user approval
- if close approval also authorizes canonical artifact promotion, that close approval must include CEO+CTO artifact-freeze approval under the global freeze rule
- if canonical artifact-freeze approval was recorded before close, close approval may remain a separate explicit user approval
- promotion remains a mechanical transition after the required approval is recorded
- step promotion from step `drafts/` to phase `artifacts/` remains mechanical after step close because artifacts remain isolated inside the active phase
- step promotion to phase `artifacts/` does not by itself promote artifacts to canonical repo truth
- phase promotion to canonical repo locations may move collected artifacts only after CEO+CTO artifact-freeze approval is recorded
- the approval record for canonical artifact promotion must be present in the same checkpoint as the movement or must be referenced as a prior recorded approval authorizing that movement

This decision preserves the two-gate model and phase-owned promotion mechanics while aligning freeze and canonical artifact promotion with the frozen global governance rule.

## APPROVAL

EXPLICIT
