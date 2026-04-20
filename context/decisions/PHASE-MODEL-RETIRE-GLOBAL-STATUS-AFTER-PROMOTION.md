# PHASE-MODEL-RETIRE-GLOBAL-STATUS-AFTER-PROMOTION

## CONTEXT

Review of the target phase model found that the draft retired local phase and step status trackers, but it still did not explicitly say what happens to the current bootstrap `context/STATUS.md` after phase-model promotion.
That left a gap between the already agreed decision that target-phase execution should not keep a duplicate status surface and the actual transition wording in the draft.

## OPTIONS

- Keep global `context/STATUS.md` as an ongoing target-phase execution surface alongside routing and workplans.
- Retire global `context/STATUS.md` at target-model promotion and make routing plus workplans the operational state surfaces.

## DECISION

The agreed target phase-model rules are:

- global `context/STATUS.md` remains a bootstrap-only operational mirror until the phase-model promotion checkpoint
- when the target phase model is promoted, global `context/STATUS.md` is retired and is not part of target phase execution
- after promotion, target operational state is reconstructed from `phases/ROUTING.md`, the active phase `WORKPLAN.md`, and scope `OPEN-ISSUES.md`
- the promotion checkpoint must remove any requirement that target-phase agents read or update global `context/STATUS.md`

This decision applies the already agreed no-duplicate-status rule all the way through the transition boundary instead of leaving it only partially reflected in the draft.

## APPROVAL

EXPLICIT
