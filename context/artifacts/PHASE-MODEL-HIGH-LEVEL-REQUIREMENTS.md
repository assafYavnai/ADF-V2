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
- one or more promoted phases at `phases/phaseNNN-<slug>/`

The meanings are:
- `phases/backlog/` holds unpromoted phase candidates
- `phases/complete/` holds closed promoted phases
- the root `phases/phaseNNN-<slug>/` paths hold promoted open phases
- exactly one promoted phase may be active at a time
- active focus is selected by `phases/ROUTING.md`

A blocked or deferred active phase does not need a separate suspended state.
If a promoted phase is deferred, it may be demoted back to backlog.

Storage class, recommended order, active focus, and step sequencing are different concerns.

The ownership rule is:
- path answers storage class
- phase number answers current recommended order among open promoted phases
- `phases/ROUTING.md` answers execution focus
- the active phase `WORKPLAN.md` answers step sequencing
- `OPEN-ISSUES.md` answers deferred unresolved work at its scope
- `context/decisions/INDEX.md` answers required global decision reads
- `HANDOFF.md`, if present, answers continuity only

The phase slug is the stable identity anchor across renumbering.
Open promoted phase numbers are recommendation-order numbers, not permanent identities.
The user may change that order during next-phase selection because information visible at closeout may differ from what was known earlier.
Completed phases preserve the number they closed under in `phases/complete/`.

Naming rules are:
- promoted open phase folders use `phases/phaseNNN-<slug>/`
- backlog candidate folders use `phases/backlog/<slug>/`
- completed phase folders use `phases/complete/phaseNNN-<slug>/`
- step folders use `stepNN-<slug>/` under the phase folder
- folder and file naming use lowercase kebab-case for slugs, with zero-padded numeric ids for promoted phases and steps

`phases/STATUS.md` is not used at this stage.

## Transition From Foundation Bootstrap

This document defines the target phase model, not the current foundation-bootstrap runtime.

Until this phase model is frozen and promoted, the current foundation-bootstrap surfaces remain authoritative for the running repository state.

This model must not become active piecemeal.
When it is promoted, the same logical checkpoint must bring routing, decision reads, and phase layout into alignment with this document before this model becomes active repo truth.

Current foundation-bootstrap root folders are transition-era exceptions until that checkpoint.
The promotion checkpoint must normalize each transition-era root folder into one target storage class:
- promoted open phase at `phases/phaseNNN-<slug>/`
- backlog candidate under `phases/backlog/`
- completed phase under `phases/complete/`

A non-conforming transition-era root folder must not remain ambiguous after the promotion checkpoint.
That same checkpoint must also rename transition-era folders into the governed naming pattern when needed.

The current intended transition mapping is:
- `phases/phase0-foundation/` becomes the active promoted foundation phase under the target model
- the current phase-model work becomes Foundation Step 1 inside that phase
- foundation normalization into full target-model compliance becomes Foundation Step 2
- `phases/phase1-Strategic_Definition/` remains a promoted but inactive/selectable phase after it is normalized into the governed target-model shape

## Routing

`phases/ROUTING.md` is the only phase-system entry point for agents.

`phases/ROUTING.md` must contain:
- the purpose of the routing surface
- the active phase pointer, or an explicit statement that no active phase is currently selected
- all resources required to reconstruct full context for the active phase when one is selected
- the required read order for the active phase when one is selected
- the local handoff lookup rule
- the current pending user decision, if any
- a mention that backlog candidates exist
- a mention that completed phases exist

`phases/ROUTING.md` must not manage decision membership itself.
It must point to `context/decisions/INDEX.md`.
`phases/ROUTING.md` must not manage step sequencing itself.
Step sequencing belongs to the active phase `WORKPLAN.md`.

If no active phase is currently selected, `phases/ROUTING.md` must say that selection is pending.
Agents must not infer an active phase when routing says none is selected.

For routing purposes, a step is selected only when the active phase `WORKPLAN.md` explicit `Current step` field points to a step folder under that phase.
If `Current step` points to a close-gate follow-up item instead, agents do not infer an active step folder unless the workplan explicitly points to one.

The required active-phase read order is:
1. active phase `CONTRACT.md`
2. active phase `WORKPLAN.md`
3. active phase `OPEN-ISSUES.md`
4. active step `CONTRACT.md`, if a step is selected
5. active step `OPEN-ISSUES.md`, if a step is selected
6. `context/decisions/INDEX.md`
7. only the decision files listed in `context/decisions/INDEX.md`
8. active step `HANDOFF.md`, if it exists
9. active phase `HANDOFF.md`, if no step-local handoff exists and a phase-local handoff exists

Default agent routing behavior is:
- do not scan `phases/backlog/` by default
- do not scan `phases/complete/` by default
- do not scan non-active promoted phases by default unless routing or the user explicitly points to them
- do not scan the full `context/decisions/` folder by default
- do not scan unrelated `HANDOFF.md` files by default

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

Transition and supersession rule:
- until this phase model is frozen and promoted, the foundation-bootstrap runtime may still use the current global `context/HANDOFF.md` decision-read list
- when this phase model is promoted, `context/decisions/INDEX.md` supersedes global `context/HANDOFF.md` as the curated decision-read surface
- the promotion checkpoint must create or update `context/decisions/INDEX.md`, update `phases/ROUTING.md` to point to it, and remove any requirement that global `context/HANDOFF.md` curate decision membership
- do not activate decision-index routing in isolation from the rest of the phase-model promotion checkpoint

Whenever a new frozen decision is saved, the matching `context/decisions/INDEX.md` update must be made in the same logical change.
That combined decision-plus-index change must end with a commit.
Do not leave a frozen decision file added without the matching `INDEX.md` update committed with it.
Do not update `INDEX.md` to reference a frozen decision that has not been committed as part of the same checkpoint.

## Backlog Candidates, Promotion, Demotion, And Order

Backlog candidates may be lightweight or mature.

A backlog candidate must have at minimum:
- a slug-based folder under `phases/backlog/`
- a `README.md` with explanation and context of the candidate

Promotion from backlog into the promoted-phases root requires:
- a fully compliant `CONTRACT.md`
- a fully compliant `WORKPLAN.md`

A phase receives its first promoted phase number when the user promotes it into the open promoted-phase set.
Open promoted phases may later be renumbered.

Renumbering rule:
- renumbering is allowed only during the next-phase selection transition
- renumbering updates open promoted phases to reflect the current reviewed recommendation order
- the slug remains the stable identity anchor across renumbering
- completed phases are not renumbered after completion
- folder renames and reference updates caused by renumbering must be completed in the same logical checkpoint

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
- artifact collection and promotion rule
- success criteria
- verification
- close gate

The phase contract must define:
- which collected phase artifacts are promotable to canonical repo locations at phase close
- the canonical promotion targets for those artifacts

## Phase Workplan

`WORKPLAN.md` is created after `CONTRACT.md`.
`WORKPLAN.md` is derived from `CONTRACT.md` and cannot expand contract scope.

The minimum required field list for a phase `WORKPLAN.md` is:
- purpose
- contract reference
- current step
- ordered implementation step list
- step dependencies or prerequisites
- default next-step rule
- close-gate follow-up steps
- change-control rule
- phase workplan close gate

No implementation starts until the phase workplan is frozen.
`WORKPLAN.md` is the authority for current step and default next-step flow inside the phase.
No separate phase-local status tracker is introduced for step sequencing.

`Current step` must be an explicit field inside `WORKPLAN.md`.
The ordered implementation step list defines the default implementation-step flow.

When a step is approved closed by the user, the next step defaults to the next item in the ordered implementation step list unless the user explicitly overrides it.
If that override changes the frozen workplan flow, the workplan must be unfrozen and revised, and the reason must be captured in the revision decision and in the revised `WORKPLAN.md`.

When all original implementation steps are completed, the phase does not move into a no-current-step state.
Instead, `WORKPLAN.md` transitions into close-gate follow-up steps as the next current-step area until phase close-gate dependencies are satisfied.

Close-gate follow-up steps may be listed in a separate section of `WORKPLAN.md` so it is clear they were added after the original implementation steps were complete.
Those follow-up steps may include:
- resolving, addressing, or explicitly deferring remaining open issues that still block phase close
- completing any remaining close-gate dependencies required before freeze can be suggested
- preparing the agent freeze recommendation and summary for user review

When all close-gate dependencies are satisfied, the next step is for the agent to suggest freeze with a summary and for the user to either approve or reject.
If the user rejects and asks for further work that changes the frozen workplan flow, that rejection triggers a quick workplan unfreeze, revision, and re-freeze before execution continues.

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
- draft-output promotion rule
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
Local `STATUS.md` is not introduced at the phase or step layer.
Local `HANDOFF.md` is optional continuity support only.

Local open issues should be resolved locally by default at the step or phase level.
If a local open issue cannot be resolved locally, it may be explicitly deferred upward to the global `OPEN-ISSUES.md`.

Global open issues act as the intake pool for deferred future work, but they are not the same thing as backlog phase candidates.
`phases/backlog/` holds explicit future phase candidates, not every deferred global open issue.
Promotion from a global open issue into `phases/backlog/<slug>/` is an explicit shaping step, not an automatic move.

A step cannot close while it still owns unresolved step-scoped open items unless those items are explicitly transferred forward.
A phase cannot close while it still owns unresolved phase-scoped open items.
To close a phase, remaining phase-scoped items must be either resolved or transferred out to backlog or general-level open items.

## Handoff

`HANDOFF.md` is optional and local in the target phase model.
It is not a boxed truth surface.
It is a continuity aid only.

Allowed local handoff locations are:
- `phases/phaseNNN-<slug>/HANDOFF.md`
- `phases/phaseNNN-<slug>/stepNN-<slug>/HANDOFF.md`

Local `HANDOFF.md` may be created only:
- when an actual handoff is needed
- when the user explicitly asks to preserve cross-session continuity for that local scope

Local `HANDOFF.md` may be updated only when a meaningful local-state change would be hard for a new agent to reconstruct from the boxed files alone.
It is not a routine progress mirror.

Local `HANDOFF.md` may contain:
- a short session summary
- what changed recently in that scope
- local blockers or risks
- temporary working notes needed for the next agent
- pointers to already authoritative local files

Local `HANDOFF.md` must not contain:
- scope authority
- current-step or next-step authority
- decision membership authority
- gate authority
- approval state that is not already reflected in the boxed files
- rules that override `CONTRACT.md`, `WORKPLAN.md`, `OPEN-ISSUES.md`, or `context/decisions/INDEX.md`

If a step-local `HANDOFF.md` exists, agents should prefer it over the phase-local `HANDOFF.md` for that step handoff.
If no step-local `HANDOFF.md` exists, agents may read the phase-local `HANDOFF.md` if it exists.

Local `HANDOFF.md` is a snapshot aid, not a continuously accumulated ledger.
It should be refreshed, replaced, or removed when it becomes stale.

The current global `context/HANDOFF.md` is part of the foundation-bootstrap runtime and not part of the target phase execution model.
When this phase model is promoted, global `context/HANDOFF.md` is no longer the decision-read authority.

## Artifacts

The required file inventory inside a promoted phase folder is:
- `CONTRACT.md`
- `WORKPLAN.md`
- `OPEN-ISSUES.md`
- one or more `stepNN-<slug>/` folders

Artifacts are authored only inside steps.
The phase does not create draft artifacts of its own.
The phase collects approved step outputs and is the only scope that may promote those collected artifacts toward canonical repo truth.

Artifact storage is boxed as:
- step `drafts/`
- phase `artifacts/`
- canonical repo destinations outside the active phase only after phase promotion

`drafts/` is optional inside a step and is created only when that step needs to author draft outputs.
`artifacts/` is optional at phase scope and is created only when the phase first collects approved step outputs.

Step draft artifacts are stored under `stepNN-<slug>/drafts/`.
The step contract must define:
- which draft outputs are promotable to phase scope
- any conditions that must be satisfied before those outputs may be collected by the phase

When a step closes, the phase scope executes step promotion under the step contract promotion rule.
Approved step outputs move from `stepNN-<slug>/drafts/` into the phase-root `artifacts/` folder.

`phases/phaseNNN-<slug>/artifacts/` holds collected phase-owned artifacts while the phase is still active.
Those artifacts remain isolated inside the phase until phase promotion.

When a phase closes, the phase scope executes phase promotion under the phase contract artifact collection and promotion rule.
Selected collected artifacts move from the phase-root `artifacts/` folder to the canonical repo locations named by the phase contract.

If a collected artifact later needs revision before phase close, it must return to an explicit step `drafts/` scope for rework rather than being revised ad hoc at phase scope.
That rework may happen in the original step or in a new explicit revision step, but it must return to step scope before being collected again by the phase.

An artifact is not ready for freeze review unless:
- its required content is complete
- its required verification is complete
- the relevant step or phase contract defines enough promotion information for the next allowed move

The artifact model does not require a separate per-artifact metadata schema at this stage.
Contracts are the authoritative source for what outputs exist, what may be promoted, and where promoted artifacts may move.

## Gates, Approvals, And Checkpoints

A step or phase moves through these states in order:
1. in progress
2. freeze ready
3. freeze gate approved
4. review-fix cycle
5. close ready
6. close gate approved
7. promotion
8. post-promotion state

A phase is freeze ready when its implementation outputs are complete enough to stop execution and enter review under the phase rules.

A step is freeze ready when its implementation outputs are complete enough to stop execution and enter review under the step rules.

Freeze ready means the scope is ready to ask for freeze-gate approval and begin the review-fix cycle.
Freeze ready does not itself close the scope.

Both freeze gate and close gate require explicit user approval.
Where a freeze event also changes trusted repo truth under the broader active context governance, that freeze approval must still satisfy the broader freeze rule.

If the freeze gate is approved:
- execution for that scope is frozen for review
- the review-fix cycle begins
- the scope remains open

A phase is close ready when:
- the review-fix cycle is complete
- review findings are addressed
- verification is rerun as required
- close-gate dependencies are satisfied
- no unresolved phase-scoped open items remain unless they are explicitly transferred out under the phase rules

A step is close ready when:
- the review-fix cycle is complete
- review findings are addressed
- verification is rerun as required
- close-gate dependencies are satisfied
- no unresolved step-scoped open items remain unless they are explicitly transferred forward under the step rules

If the close gate is approved:
- the scope closes
- promotion runs next as a mechanical transition
- promotion is not a separate approval gate

Promotion execution is owned by the phase scope because the phase workplan owns completion flow.

For step close and promotion:
- the phase scope executes step promotion under the step contract promotion rule
- the phase scope updates the phase workplan and any affected phase-local files in the same logical checkpoint
- after step promotion, control returns to phase scope for the next current step

For phase close and promotion:
- the phase scope executes phase promotion
- the phase moves to `phases/complete/` with the number it closed under
- completion may also move outputs to other destinations if that is defined in the phase contract
- the phase scope updates `phases/ROUTING.md` in the same logical checkpoint
- after phase promotion, routing either points to the selected next active phase or explicitly says that no active phase is selected and the system is idle / waiting for input

Closing a phase does not require immediate next-phase selection.
Next-phase selection remains a separate transition after phase promotion.

During next-phase selection, the user may choose the next active phase from:
- already promoted open phases at the root
- backlog candidates
- a newly shaped candidate

If the user selects a backlog candidate or newly shaped candidate, that candidate is promoted into the open promoted-phase set during the same transition.
After the user selects the next active phase, the open promoted phases are renumbered to reflect the current reviewed recommendation order, and `phases/ROUTING.md` is updated to point to the selected active phase.

For now, only explicit user input exits the idle routing state.
Future script governance may define additional governed triggers.

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

For next-phase selection and renumbering:
- routing updates, folder renames, and reference updates caused by the reviewed selection order must be part of the same logical checkpoint
- do not leave promoted-phase numbering and routing partially updated across checkpoints

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
