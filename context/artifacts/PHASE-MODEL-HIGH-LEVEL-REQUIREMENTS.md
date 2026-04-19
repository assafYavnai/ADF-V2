## STATUS

DRAFT

## OWNER

CEO

## FREEZE-GATE

READY FOR REVIEW

## PROMOTED-TARGET

`phases/PHASE-MODEL.md`

# PHASE-MODEL

This artifact is the review-ready draft of the ADF phase model.
It remains draft until it is frozen under the global freeze rule.
It is written to be script-ready, meaning detailed enough to serve both as a requirements surface and as a design surface for later script enforcement.

## Purpose

This model defines:
- what a phase is
- how phases are routed and stored
- how contracts, workplans, and steps relate
- how decisions, open issues, and artifacts behave across layers
- how phase and step approvals, freezes, promotions, and demotions are governed

## Phase System Layout

The `phases/` layer uses these top-level states:
- `phases/ROUTING.md`
- `phases/backlog/`
- `phases/complete/`
- one active promoted phase at `phases/phaseNNN-<slug>/`

The meanings are:
- `phases/backlog/` holds unpromoted phase candidates
- `phases/complete/` holds closed promoted phases
- the root `phases/phaseNNN-<slug>/` path holds the one currently active promoted phase

A blocked or deferred active phase does not need a separate suspended state.
If a promoted phase is deferred, it may be demoted back to backlog.

Promoted phase identity and execution order are different concerns.
The promoted phase folder keeps one stable phase id in its path.
Execution order is carried by routing and current-state tracking, not by the folder path.

Naming rules are:
- promoted active phase folders use `phases/phaseNNN-<slug>/`
- backlog candidate folders use `phases/backlog/<slug>/`
- completed phase folders use `phases/complete/phaseNNN-<slug>/`
- step folders use `stepNN-<slug>/` under the phase folder
- folder and file naming use lowercase kebab-case for slugs, with zero-padded numeric ids for promoted phases and steps

`phases/STATUS.md` is not used at this stage.

## Routing

`phases/ROUTING.md` is the only phase-system entry point for agents.

`phases/ROUTING.md` must contain:
- the purpose of the routing surface
- the active phase pointer
- all resources required to reconstruct full context for the active phase
- the required read order for the active phase
- the current pending user decision, if any
- a mention that backlog candidates exist
- a mention that completed phases exist

`phases/ROUTING.md` must not manage decision membership itself.
It must point to `context/decisions/INDEX.md`.

The required active-phase read order is:
1. active phase `CONTRACT.md`
2. active phase `WORKPLAN.md`
3. active phase `OPEN-ISSUES.md`
4. active step `CONTRACT.md`, if a step is selected
5. active step `OPEN-ISSUES.md`, if a step is selected
6. `context/decisions/INDEX.md`
7. only the decision files listed in `context/decisions/INDEX.md`

Default agent routing behavior is:
- do not scan `phases/backlog/` by default
- do not scan `phases/complete/` by default
- do not scan other phases by default
- do not scan the full `context/decisions/` folder by default

## Decisions

Frozen decisions are global by nature and are written only under `context/decisions/`.

Decision filename rule:
- `UPPERCASE-WITH-HYPHENS.md`

Each decision file must contain:
- `CONTEXT`
- `OPTIONS`
- `DECISION`
- `APPROVAL`

A decision is frozen only after explicit CEO+CTO approval under the global freeze rule.

Decision save rules are:
- save a decision when a real fork is closed and approved
- do not save implicit assumptions as frozen decisions
- do not save routine progress as a decision unless it changes frozen repo truth

`context/decisions/INDEX.md` is the curated decision-read surface for current truth.
It is not a historical catalog and not a full folder listing.

`context/decisions/INDEX.md` must contain:
- a short purpose statement
- the rule that agents read only listed decisions by default
- a `Required decision files` section
- an optional one-line reason for each listed decision

The `Required decision files` list must include:
- new decisions that affect current active truth
- older decisions still required to understand current active truth

The `Required decision files` list must exclude:
- unrelated historical decisions
- decisions no longer needed for current understanding
- unfrozen discussion artifacts

Agents must update `context/decisions/INDEX.md`:
- whenever a new frozen decision changes active truth
- whenever the active phase or current truth changes such that different older decisions are now required
- whenever a listed decision is no longer required to reconstruct current truth correctly

Default agent decision-read behavior is:
1. read `context/decisions/INDEX.md`
2. read only the listed decision files
3. do not scan the full `context/decisions/` folder by default

Whenever a new frozen decision is saved, the matching `context/decisions/INDEX.md` update must be made in the same logical change.
That combined decision-plus-index change must end with a commit.
Do not leave a frozen decision file added without the matching `INDEX.md` update committed with it.
Do not update `INDEX.md` to reference a frozen decision that has not been committed as part of the same checkpoint.

## Backlog Candidates, Promotion, And Demotion

Backlog candidates may be lightweight or mature.

A backlog candidate must have at minimum:
- a slug-based folder under `phases/backlog/`
- a `README.md` with explanation and context of the candidate

Promotion from backlog to active phase requires:
- a fully compliant `CONTRACT.md`
- a fully compliant `WORKPLAN.md`

A phase receives its promoted phase number only when the user selects it for promotion.

Demotion of a promoted phase back to backlog requires explicit user approval.

When a promoted phase is demoted back to backlog:
- it moves to `phases/backlog/<slug>/`
- its phase number is removed from the folder path
- its former promoted id is preserved in the backlog candidate `README.md` for history

The preserved former promoted id uses an explicit field such as:
- `Former promoted id: phaseNNN`

If the backlog candidate later becomes a full contract-bearing phase candidate, that preserved field may move into `CONTRACT.md`.

## Phase Contract

A phase is an ADF work container governed by explicit repo contracts.

The minimum required field list for a phase `CONTRACT.md` is:
- goal
- scope
- out-of-scope
- outputs
- success criteria
- verification
- close gate

Phase and step contracts must each define a promotion rule for their artifacts.

## Phase Workplan

`WORKPLAN.md` is created after `CONTRACT.md`.
`WORKPLAN.md` is derived from `CONTRACT.md` and cannot expand contract scope.

The minimum required field list for a phase `WORKPLAN.md` is:
- purpose
- contract reference
- ordered step list
- step dependencies or prerequisites
- default next-step rule
- change-control rule
- phase workplan close gate

No implementation starts until the phase workplan is frozen.

When a step is approved closed by the user, the next step defaults to the next item in the workplan unless the user explicitly overrides it.
Any override must be documented with the reason.

## Workplan Change Control

`WORKPLAN.md` may later be unfrozen because of discoveries during implementation.

The `WORKPLAN.md` unfreeze and re-freeze process is:
1. identify the affected part of the current frozen `WORKPLAN.md`
2. stop execution against the affected workplan portion
3. record the reason the workplan must be unfrozen
4. mark the workplan as unfrozen in its own state wording
5. update related scope-local files if needed, such as affected `OPEN-ISSUES.md`
6. revise `WORKPLAN.md` within frozen contract scope only
7. clearly show what changed and why
8. present the revised workplan for user review
9. after approval, re-freeze the workplan
10. resume execution only under the re-frozen workplan

The unfreeze trigger must be explicit, not inferred quietly.
Unfreezing a workplan does not unfreeze the phase contract.
Execution may continue only on unaffected workplan portions if that work does not rely on the outdated section.
Affected work must pause until the revised workplan is approved and re-frozen.

Allowed changes during workplan unfreeze are:
- reprioritizing existing steps
- splitting one step into smaller steps
- merging existing steps
- reordering steps
- revising step prerequisites or dependencies
- refining step verification detail
- adding a new step if it stays fully inside frozen contract scope
- removing a step if its intent is still fully covered elsewhere inside frozen contract scope
- changing default next-step flow inside the workplan if it stays within frozen contract scope

Forbidden changes during workplan unfreeze are:
- changing the phase goal
- changing phase scope
- changing out-of-scope boundaries
- changing required outputs
- changing success criteria
- changing contract-level verification intent
- changing close-gate meaning
- introducing work that belongs to a different phase identity

Workplan unfreeze may change execution design.
Workplan unfreeze may not change phase identity.

Frozen phase scope is not allowed to be breached.
If requested work does not fit the frozen phase purpose, outputs, or exit gate, it is out of scope unless `WORKPLAN.md` is explicitly unfrozen and revised.
If the work still does not fit after that test, it must become a different phase candidate.

## Steps

The minimum required step contract is:
- goal
- scope
- prerequisites
- outputs
- verification
- close gate

The exact required file inventory inside a step folder is:
- `CONTRACT.md`
- `OPEN-ISSUES.md`

Step folders use `stepNN-<slug>/`.

## Open Issues

Each layer has its own `OPEN-ISSUES.md`.

Open-items scope is layered as:
- general
- phase
- step

Phase-local files live at the phase scope root.
Step-local files live at the step scope root.

Local `OPEN-ISSUES.md` files live at the scope root, not inside a nested `context/` folder.

Phase-local `OPEN-ISSUES.md` uses:
- `phases/phaseNNN-<slug>/OPEN-ISSUES.md`

Step-local `OPEN-ISSUES.md` uses:
- `phases/phaseNNN-<slug>/stepNN-<slug>/OPEN-ISSUES.md`

Only `OPEN-ISSUES.md` is required locally at this stage.
Local `STATUS.md` and `HANDOFF.md` are not introduced at the phase or step layer at this stage.

Local open issues should be resolved locally by default at the step or phase level.
If a local open issue cannot be resolved locally, it may be explicitly deferred upward to the global `OPEN-ISSUES.md`.

Global open issues act as the intake pool for deferred future work, but they are not the same thing as backlog phase candidates.
`phases/backlog/` holds explicit future phase candidates, not every deferred global open issue.
Promotion from a global open issue into `phases/backlog/<slug>/` is an explicit shaping step, not an automatic move.

A step cannot close while it still owns unresolved step-scoped open items unless those items are explicitly transferred forward.
A phase cannot close while it still owns unresolved phase-scoped open items.
To close a phase, remaining phase-scoped items must be either resolved or transferred out to backlog or general-level open items.

## Artifacts

The required file inventory inside a promoted phase folder is:
- `CONTRACT.md`
- `WORKPLAN.md`
- `OPEN-ISSUES.md`
- one or more `stepNN-<slug>/` folders

A phase or step creates `artifacts/` when it first needs to hold draft artifacts.
`artifacts/` is optional in scopes that do not yet have draft artifacts.

Step draft artifacts are stored under `stepNN-<slug>/artifacts/`.
When a step artifact is frozen, it is promoted from `stepNN-<slug>/artifacts/` to the step root by default.
If a step artifact is later demoted, it moves back from the step root into `stepNN-<slug>/artifacts/`.

When a step closes, artifacts at step root promote by the step contract promotion rule.
If the step contract does not define a different destination, the default step promotion destination is the phase-root `artifacts/` folder.
If neither the step contract nor the artifact metadata defines a destination where one is required, the artifact is not ready for freeze review.

Phase draft artifacts are stored under `phases/phaseNNN-<slug>/artifacts/`.
When a phase artifact is frozen, it is promoted from the phase `artifacts/` folder to the phase root by default.
If a phase artifact is later demoted, it moves back from the phase root into the phase `artifacts/` folder.

When a phase closes, artifacts at phase root promote by the phase contract promotion rule.
If the phase contract does not define a different destination, the default phase promotion destination is the canonical repo location explicitly named by the artifact promotion target.
If neither the phase contract nor the artifact metadata defines a destination where one is required, the artifact is not ready for freeze review.

## Gates, Approvals, And Checkpoints

A phase is ready for freeze review when its required outputs are complete and verified, its contract and workplan requirements are satisfied, and no unresolved phase-scoped open items remain unless they are explicitly transferred out under the phase rules.

A step is ready for freeze review when its required outputs are complete and verified, its step contract requirements are satisfied, and no unresolved step-scoped open items remain unless they are explicitly transferred forward under the step rules.

Satisfying a phase or step freeze-review gate means the work is ready to ask for freeze approval.
Actual freeze requires explicit approval from both CEO and CTO under the global freeze rule.

A completed phase is moved to `phases/complete/` after the user approves the phase close gate.
Completion may also move outputs to other destinations if that is defined in the phase contract.

Approvals must be recorded explicitly in repo files.
Approval is never inferred from progress, silence, or downstream edits.

Approval is recorded:
- in the file being approved, by changing its approval or status wording
- in the relevant tracker files, so current truth reflects the approval
- in a global decision file when the approval freezes or changes repo truth in a way that the decision rules require

For contracts and workplans:
- the approved file must explicitly say it is frozen or approved
- if a workplan is re-frozen after unfreeze, that state change must be recorded in the workplan itself

For step and phase closure:
- closure approval must be reflected in the governing workplan and any affected `OPEN-ISSUES.md`
- if closure causes promotion, the related artifact or folder move must be part of the same logical checkpoint

For decisions:
- decision approval is recorded in the decision file under `APPROVAL`
- the matching `context/decisions/INDEX.md` update must be part of the same checkpoint

Each approval that changes repo truth must end in a commit.
That commit must include all files needed to make the approved state self-consistent.

## Script Readiness

Script governance is explicitly out of scope as a current implementation layer in this draft.

The frozen phase-model draft must still be script-ready.
Script-ready means the document is detailed enough to be used both:
- as a requirements list for script implementation
- as a design document for script implementation

Any future script layer must enforce the frozen model and must not redefine it.

## Review Note

This draft is written as the review-ready pre-canonical phase model.
It is intended to be reviewed as a complete model with no open questions or deferred model holes before freeze approval is requested.
