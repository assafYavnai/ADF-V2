# PHASE-MODEL-ROOT-SUPPORT-FILE-INVENTORY

## CONTEXT

The seven-finding review found that the phase-model artifact promotes to `phases/PHASE-MODEL.md`, while the target `phases/` root inventory listed only routing, backlog, complete, and promoted phase folders.
That left future script enforcement with an impossible choice: reject the promoted canonical phase model file or invent an undocumented root-file exception.

## PUSHBACK

The pushback was:
- `PHASE-MODEL.md` was the artifact's promoted target
- the phase root inventory did not explicitly allow it
- the target model also says no structural exceptions are allowed
- a script-ready model needs a closed, enforceable root inventory

## DISCUSSION SUMMARY

The approved resolution is to make `phases/PHASE-MODEL.md` an explicit canonical support file at the phase-system root.
This is not an exception to the no-exceptions rule because it is part of the governed closed inventory.

`PHASE-MODEL.md` defines the phase system itself.
It therefore belongs at the phase-system layer root beside `ROUTING.md`.
It is not a lifecycle state folder, not a phase candidate, not a promoted phase, and not numbered.

## OPTIONS

- Move the promoted target somewhere outside `phases/`.
- Keep `phases/PHASE-MODEL.md` as an implicit exception.
- Add `phases/PHASE-MODEL.md` as an explicit allowed canonical support file in the phase-root inventory.

## DECISION

The agreed target phase-model rules are:

- `phases/PHASE-MODEL.md` is the canonical phase-system model file after promotion
- `phases/PHASE-MODEL.md` is a fixed canonical support file for the `phases/` layer
- it is not a lifecycle state, phase candidate, promoted phase, or numbered phase folder
- the allowed `phases/` root inventory is closed
- the `phases/` root may contain only:
  - `PHASE-MODEL.md`
  - `ROUTING.md`
  - `backlog/`
  - `complete/`
  - promoted phase folders shaped as `phaseNNN-<slug>/`
- no other root support files are allowed unless the phase model explicitly adds them to the root inventory
- the phase-model promotion checkpoint must promote the draft artifact into `phases/PHASE-MODEL.md`

This decision resolves the root-inventory finding while preserving deterministic no-exceptions enforcement.

## APPROVAL

EXPLICIT
