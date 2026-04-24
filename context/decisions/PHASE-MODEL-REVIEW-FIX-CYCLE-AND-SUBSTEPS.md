# PHASE-MODEL-REVIEW-FIX-CYCLE-AND-SUBSTEPS

## CONTEXT

The fresh review of `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` found that the draft defined `review-fix-cycle` as a lifecycle state but did not define where review findings, review-driven fixes, verification, or transfer decisions live while that state is active.

The same discussion also raised whether the model should include step and substep structure.

## PUSHBACK

The review-fix cycle was not yet script-ready because a contextless agent or future script could record that a phase or step is in `review-fix-cycle`, but would still have to invent:
- where review-fix items are listed
- how `Current step` points to active review work
- what states a review-fix item may have
- how review-fix work links to step rework, artifacts, open issues, or verification
- when the review-fix cycle is complete

## DISCUSSION SUMMARY

The approved first-principles answer was to use the existing owner instead of adding another tracker.
Because `WORKPLAN.md` already owns runtime state, it also owns review-fix cycle current work.

The user then asked about step and substep.
The approved rule is that a phase step remains the formal governed unit.
Substeps may exist only as local descriptive planning inside a step.
They do not become routed entities, folders, lifecycle owners, promotion units, numbered execution units, or close-gate owners.
If a substep needs its own contract, gate, artifacts, or user approval, it must become a real governed step.

## OPTIONS

- Add a separate review-fix tracker file.
- Treat review-fix work as informal prose inside handoff or status.
- Keep review-fix current work inside the phase `WORKPLAN.md`.
- Add substeps as a new governed structural layer.
- Keep substeps as local, non-governed planning only.

## DECISION

The agreed target phase-model rules are:

- phase `WORKPLAN.md` owns review-fix cycle current work
- `review-fix` is an allowed `Current step type`
- `Current step` may point to a review-fix item id shaped as `review-<slug>`
- a compliant phase `WORKPLAN.md` must provide a `## Review-Fix Cycle` section when lifecycle state is `review-fix-cycle`
- `## Review-Fix Cycle` items must include item id, title, source, scope, state, owner, next action, closure condition, verification, and linked surface
- allowed review-fix item states are `open`, `in-progress`, `fixed`, `verified`, `closed`, and `transferred`
- the review-fix cycle is complete only when every review-fix item is `closed` or `transferred`
- if a review-fix item requires step rework, the linked surface must point to the affected step or artifact
- if a review-fix item is transferred rather than closed, the linked surface must point to the receiving `OPEN-ISSUES.md` entry or other governed target
- routing does not select a step folder for review-fix work unless the active review-fix item explicitly links to step rework

Substep rules are:

- substeps are allowed only as local descriptive planning inside a step
- substeps are not a governed routing layer
- substeps do not receive folders
- substeps do not own lifecycle state, promotion, numbering, or close gates
- if a substep needs its own contract, gate, artifacts, or user approval, it must become a real governed step
- review-fix items are not substeps; they are governed runtime items in the phase `WORKPLAN.md`

This decision resolves the review-fix current-work schema finding without adding another tracker layer, and prevents substeps from becoming a hidden third governance layer.

## APPROVAL

EXPLICIT
