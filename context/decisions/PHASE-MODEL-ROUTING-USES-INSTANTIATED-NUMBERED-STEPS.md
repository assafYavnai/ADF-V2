# PHASE-MODEL-ROUTING-USES-INSTANTIATED-NUMBERED-STEPS

## CONTEXT

A deeper carry-through audit of the target phase model found that the routing section in the draft still used older generic wording about a `step folder`, even after the virtual-step and former-step model had already been agreed and frozen.
That left one partial-application gap between the routing rules and the later step-instantiation rules.

## OPTIONS

- Leave routing with the old generic `step folder` wording and rely on readers to infer that it now means only instantiated numbered steps.
- Explicitly align routing with the virtual-step model by saying that routing only recognizes instantiated numbered step folders under `steps/` as active steps.

## DECISION

The agreed target phase-model rules are:

- for routing purposes, a step is selected only when the active phase `WORKPLAN.md` explicit `Current step` field points to an instantiated numbered step folder under `steps/`
- if `Current step` points to a freeze-ready preparation item, review-fix item, close-gate follow-up item, or any other non-step item, agents do not infer an active step folder
- preserved former-step folders are not active steps for routing unless they are re-instantiated as numbered step folders

This decision supersedes only the older generic `step folder` routing wording where it conflicts with the already approved virtual-step and former-step model.

## APPROVAL

EXPLICIT
