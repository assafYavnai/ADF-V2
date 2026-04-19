# PHASE-MODEL-PROMOTED-ROOT-ORDER-AND-TRANSITION

## CONTEXT

The review of `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` raised a structural pushback on the phase-tree model.
The draft described a target `phases/` root with one active promoted phase, but the live repository still contained multiple root phase folders from the foundation-bootstrap era.
Without an explicit transition rule, freezing the draft would make the repository contradict itself.

The discussion also reopened an earlier assumption about root phase folders.
An earlier recommendation treated the root promoted-phase path as meaning active.
That assumption was challenged and rejected during review because active focus is a routing concern, not a path concern.

## PUSHBACK

The core pushback was:
- the target phase layout in the draft contradicted the live tree
- the draft did not yet say how current root phase folders should be reclassified or normalized
- if root phase folders were treated as meaning active, routing would become partly duplicated
- if promoted phases kept stable numbers with no other recommendation surface, the user would be left with an arbitrary candidate list when choosing what should happen next
- if phase close and next-phase selection were merged, the system could get stuck with a closed phase that could not be promoted to complete until the next phase was chosen

## DISCUSSION SUMMARY

The discussion returned to first principles instead of treating the current tree as sacred.

The first clarification was ownership.
The agreed ownership split is:
- path answers storage class
- phase number answers current recommended order among open promoted phases
- `phases/ROUTING.md` answers execution focus
- the active phase `WORKPLAN.md` answers step sequencing

This replaced the earlier assumption that the root phase path itself must encode active status.
Active status belongs to routing, not to the folder path.

The second clarification was phase numbering.
The user challenged the idea of keeping promoted numbers stable forever when no separate artifact was carrying recommendation order.
The agreed answer was that promoted phase numbers are recommendation-order numbers for open promoted phases, not permanent identities.
The slug is the stable identity anchor across renumbering.
The user may change the recommended order when choosing the next phase because information visible at closeout may be different from what was known earlier.

The third clarification was transition handling.
The draft needed to say explicitly that the current foundation-bootstrap root folders are transition-era exceptions until the phase-model promotion checkpoint normalizes them into the governed shape.

The fourth clarification was operational sequencing.
Phase close gate and next-phase selection are separate transitions.
Closing the current phase must not depend on immediate choice of the next phase.
Only after close does the next-phase selection transition run, update routing, and renumber promoted open phases.

## OPTIONS

- Keep the earlier assumption that only one active promoted phase may exist at the root and make root path imply active status.
- Allow multiple promoted phases at the root, with routing selecting exactly one active phase.
- Keep promoted phase numbers stable forever and put recommendation somewhere else later.
- Treat promoted phase numbers as the current recommended order among open promoted phases.
- Keep phase close and next-phase selection as one combined gate.
- Separate phase close from next-phase selection.

## DECISION

The agreed target phase-model rules are:

- `phases/` root may contain one or more promoted open phases
- exactly one promoted phase may be active at a time
- `phases/ROUTING.md` selects the currently active promoted phase
- non-active promoted phases may remain at the root as promoted but inactive/selectable phases

- the ownership split is:
  - path answers storage class
  - phase number answers current recommended order among open promoted phases
  - `phases/ROUTING.md` answers execution focus
  - the active phase `WORKPLAN.md` answers step sequencing

- promoted phase numbers are recommendation-order numbers for open promoted phases
- promoted phase numbers are not permanent identities
- the phase slug is the stable identity anchor across renumbering
- completed phases preserve the number they closed under

- renumbering is allowed only during the next-phase selection transition
- renumbering updates open promoted phases to reflect the reviewed recommendation order
- folder renames and reference updates caused by renumbering must be completed in the same logical checkpoint

- phase close gate and next-phase selection are separate transitions
- the phase close gate asks only whether the current active phase may close
- if the phase close gate is approved, the phase closes and moves to `phases/complete/`
- routing may temporarily state that no active phase is selected yet
- next-phase selection happens after close as a separate transition
- during next-phase selection, the user may choose the next active phase from:
  - already promoted open phases at the root
  - backlog candidates
  - a newly shaped candidate

- until the phase model is frozen and promoted, the current foundation-bootstrap tree remains a transition-era exception
- when the phase model is promoted, the same logical checkpoint must normalize each transition-era root folder into one governed storage class and rename it into the governed naming pattern where required

- the current intended transition mapping is:
  - `phases/phase0-foundation/` becomes the active promoted foundation phase
  - the current phase-model work becomes Foundation Step 1 inside that phase
  - foundation normalization into full target-model compliance becomes Foundation Step 2
  - `phases/phase1-Strategic_Definition/` remains a promoted but inactive/selectable phase after normalization into governed target-model shape

This decision defines the target model and its transition rule.
It does not itself activate the target model before the phase-model promotion checkpoint is executed.

## APPROVAL

EXPLICIT
