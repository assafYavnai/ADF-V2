# PHASE-MODEL-OPEN-ISSUES-TRANSITION-TRIAGE

## CONTEXT

Review of the phase-model draft raised a pushback that deferred foundation work could be split across two authority surfaces.

The current bootstrap model originally used `context/OPEN-ISSUES.md` as the one canonical deferred-items file.
The target phase model introduces scope-local `OPEN-ISSUES.md` files.
During this transition, deferred foundation-phase concerns that must survive Foundation Step 1 promotion are now tracked in `phases/phase0-foundation/OPEN-ISSUES.md`.

Without an explicit boundary, a later agent could treat `context/OPEN-ISSUES.md` and `phases/phase0-foundation/OPEN-ISSUES.md` as competing stores for the same scope.

## OPTIONS

- Move all foundation-scoped items back to `context/OPEN-ISSUES.md` until full phase-model promotion.
- Treat both files as interchangeable deferred-item stores.
- Keep both files during transition, but define a strict scope boundary and require promotion-time triage.

## DECISION

During the current transition:
- `context/OPEN-ISSUES.md` remains the global/bootstrap deferred-items surface
- `phases/phase0-foundation/OPEN-ISSUES.md` owns foundation-phase deferred work that must survive Foundation Step 1 and later step promotion
- the two files must not hold competing entries for the same scoped item
- if an item is foundation-phase scoped, it belongs in `phases/phase0-foundation/OPEN-ISSUES.md`
- if an item is global, bootstrap-wide, or not yet shaped into a phase scope, it belongs in `context/OPEN-ISSUES.md`

At phase-model promotion:
- the promotion checkpoint must triage `context/OPEN-ISSUES.md`
- foundation-scoped items must be moved into `phases/phase0-foundation/OPEN-ISSUES.md`
- only true global/bootstrap items may remain in `context/OPEN-ISSUES.md`
- the triage and any moved items must be committed in the same logical checkpoint so git preserves the transfer audit trail

This decision supersedes `context/decisions/MANUAL-CONTEXT-STRUCTURE-AND-TRACKERS.md` only where that older decision says `context/OPEN-ISSUES.md` is the one canonical deferred-items file for all deferred work.
The older decision remains valid for bootstrap/global deferred items that have not been assigned to a phase or step scope.

## APPROVAL

EXPLICIT
