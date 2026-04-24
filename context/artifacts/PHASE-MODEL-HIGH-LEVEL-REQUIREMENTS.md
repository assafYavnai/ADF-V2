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
- all step folders live under the phase-local `steps/` namespace
- official instantiated step folders use `steps/stepNN-<slug>/` under the phase folder
- preserved former-step folders use `steps/<slug>/` when an instantiated step loses its execution number
- folder and file naming use lowercase kebab-case for slugs, with zero-padded numeric ids for promoted phases and steps

`phases/STATUS.md` is not used at this stage.

## Transition From Foundation Bootstrap

This document defines the target phase model, not the current foundation-bootstrap runtime.

Until this phase model is frozen and promoted, the current foundation-bootstrap surfaces remain authoritative for the running repository state.

This model must not become active piecemeal.
When it is promoted, the same logical checkpoint must bring routing, decision reads, and phase layout into alignment with this document before this model becomes active repo truth.

No target-model structural exceptions are allowed.
Current non-target structures remain part of the current bootstrap runtime only and do not count as valid target-model shapes.
The promotion checkpoint must normalize each affected current structure into one governed target storage class:
- promoted open phase at `phases/phaseNNN-<slug>/`
- backlog candidate under `phases/backlog/`
- completed phase under `phases/complete/`

A non-conforming current root folder must not remain ambiguous after the promotion checkpoint.
That same checkpoint must also rename current folders into the governed naming pattern when needed.
The target model does not permit carrying forward a non-compliant structure as an exception.

Bootstrap-only current-state surfaces remain bootstrap-only until the promotion checkpoint.
Until that checkpoint:
- global `context/HANDOFF.md` remains part of the current foundation-bootstrap runtime
- global `context/STATUS.md` remains the bootstrap thin operational mirror

When the target phase model is promoted:
- global `context/STATUS.md` is retired and is not part of target phase execution
- target operational state is reconstructed from `phases/ROUTING.md`, the active phase `WORKPLAN.md`, and scope `OPEN-ISSUES.md`
- the promotion checkpoint must remove any requirement that target-phase agents read or update global `context/STATUS.md`
- the context layer entry surface must point agents into `phases/ROUTING.md` for phase execution
- `AGENTS.md` remains the top-level layer entry funnel and is updated only when top-level layer entry points change
- `CLAUDE.md` and `GEMINI.md` remain static funnel stubs unless an LLM-specific setting is required
- implementation is only through this phase-model document until the phase model is promoted; live bootstrap files must not be changed early
- the promotion checkpoint must triage `context/OPEN-ISSUES.md`, move foundation-scoped items into `phases/phase0-foundation/OPEN-ISSUES.md`, and leave only true global/bootstrap items in the global file so the post-transition structure is clean
- the promotion checkpoint must migrate legacy phase step folders into the `steps/` namespace; any root-level `stepNN-<slug>/` folder becomes `steps/stepNN-<slug>/`, any root-level preserved former-step `<slug>/` folder becomes `steps/<slug>/`, and all workplan, routing, open-issues, handoff, artifact, and decision references affected by the move must be updated in the same logical checkpoint

The current intended transition mapping is:
- `phases/phase0-foundation/` becomes the active promoted foundation phase under the target model
- the current phase-model work becomes Foundation Step 1 inside that phase
- foundation normalization into full target-model compliance becomes Foundation Step 2
- `phases/phase1-Strategic_Definition/` remains a promoted but inactive/selectable phase after it is normalized into the governed target-model shape
- `phases/backlog/system-definition/` is normalized as a folder-based backlog candidate by keeping its backlog `WORKPLAN.md` and removing the nested legacy `phases/` subtree
- if `system-definition` is later selected for promotion, that retained workplan may be reused if still compliant, and the promotion checkpoint must add the missing compliant phase contract and the rest of the required promoted-phase inventory

## Agent Entry And Boxed Traversal

`AGENTS.md` is the top-level agent entry funnel.
It is not the phase router and must not duplicate the current phase, current step, or active-task route.
It also must not maintain a full map, index, inventory, layer summary, or repository description.

`AGENTS.md` names only the top-level layer boxes and their entry-point paths.
Agents reconstruct the operating structure by opening those entry-point files and then following only the links, pointers, and instructions provided by each opened box.

The target `AGENTS.md` file has exactly two sections:
- `Summary`
- `Layers`

`Summary` must explain the boxed traversal goal, the agent's goal to populate a working structure map by traversal, and the guardrail against scanning or inventing structure outside provided pointers.
`Layers` must be YAML with explicit `name` and repo-relative `path` entries.
Layer explanations and sublayer routing are owned by the layer entry files themselves, not by `AGENTS.md`.

The current target top-level layers are:
- `governance`, entered through `./RULES.md`
- `context`, entered through `./CONTEXT.md`

`governance` is the layer for global ADF governance such as rules and roles.
Adding a governance surface, such as a role file, should be handled inside the governance layer unless it creates a genuinely new top-level layer.
`context` is the layer for current operating context, including the later path into phase routing.

`AGENTS.md` changes only when a top-level layer entry point is added, removed, or renamed.
It does not change for normal phase execution, phase selection, step movement, or local context updates.

Tool-specific stubs such as `CLAUDE.md` and `GEMINI.md` are static funnel files.
They point their agents to `AGENTS.md` and do not change unless an LLM-specific setting is required.
They must not change for phase execution, phase selection, routing movement, context movement, or normal repo work.

The target `AGENTS.md` structure to apply when the phase model is promoted is:

````md
# ADF Agent Entry

## Summary

This file is the top-level entry funnel for agents working in ADF.

The agent's first goal is to reconstruct the current ADF operating structure by traversing the declared layers below.

Agents must read the YAML list under `Layers`.
Each YAML item is a top-level layer entry point.

For each YAML item:
1. Read `name` as the layer name.
2. Read `path` as the layer entry-point file.
3. Open that `path`.
4. Treat the opened file as the authority for that layer.
5. Record the layer, its purpose, and any next pointers it provides in the agent's working structure map.
6. Follow only the links, pointers, and instructions provided inside that opened layer file.
7. Continue traversal only through pointers provided by the current opened box.

ADF uses a boxed traversal model.
Each layer is a box.
Opening a box may reveal more boxes.
Agents construct the operating structure by traversing provided pointers, not by scanning the repository or inventing a global map.

**Guardrail: agents must only follow the links each layer / box provides. Do not infer missing structure, scan outside the provided traversal path, or build a separate global map unless the user explicitly asks.**

After traversal, the agent should work only inside the reconstructed structure and the user's explicit request.

## Layers

```yaml
layers:
  - name: governance
    path: ./RULES.md
  - name: context
    path: ./CONTEXT.md
```
````

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

For routing purposes, a step is selected only when the active phase `WORKPLAN.md` explicit `Current step` field points to an instantiated numbered step folder under `steps/`.
If `Current step` points to a freeze-ready preparation item, close-gate follow-up item, or any other non-step item instead, agents do not infer an active step folder.

The required active-phase read order is:
1. active phase `CONTRACT.md`
2. active phase `WORKPLAN.md`
3. active phase `OPEN-ISSUES.md`
4. active step `CONTRACT.md` under `steps/`, if a step is selected
5. active step `OPEN-ISSUES.md` under `steps/`, if a step is selected
6. `context/decisions/INDEX.md`
7. only the decision files listed in `context/decisions/INDEX.md`
8. active step `HANDOFF.md`, if it exists
9. active phase `HANDOFF.md`, if no step-local handoff exists and a phase-local handoff exists

Default agent routing behavior is:
- do not scan `phases/backlog/` by default
- do not scan `phases/complete/` by default
- do not scan non-active promoted phases by default unless routing or the user explicitly points to them
- do not scan preserved former-step folders by default unless the active phase `WORKPLAN.md` or phase `OPEN-ISSUES.md` explicitly points to them
- do not scan the full `context/decisions/` folder by default
- do not scan unrelated `HANDOFF.md` files by default

## Decisions

Frozen decisions are global by nature and are written only under `context/decisions/`.

In the target phase model, `context/decisions/` contains only:
- frozen decision files
- the canonical support file `context/decisions/INDEX.md`

`context/decisions/INDEX.md` is a governed support file, not a frozen decision entry.
It does not use the decision-entry contract of `CONTEXT`, `OPTIONS`, `DECISION`, and `APPROVAL`.

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
- until that promotion checkpoint, the current bootstrap contract that `context/decisions/` holds frozen decisions only remains authoritative
- when the phase model is promoted, the promotion checkpoint also changes the `context/decisions/` folder contract from `frozen decisions only` to `frozen decisions plus the canonical support file INDEX.md`
- that same promotion checkpoint must create or update `context/decisions/INDEX.md`, update `phases/ROUTING.md` to point to it, update `CONTEXT.md`, update `context/decisions/README.md`, and remove any requirement that global `context/HANDOFF.md` curate decision membership
- do not activate decision-index routing in isolation from the rest of the phase-model promotion checkpoint

Whenever a new frozen decision is saved, the matching `context/decisions/INDEX.md` update must be made in the same logical change.
That combined decision-plus-index change must end with a commit.
Do not leave a frozen decision file added without the matching `INDEX.md` update committed with it.
Do not update `INDEX.md` to reference a frozen decision that has not been committed as part of the same checkpoint.

## Backlog Candidates, Promotion, Demotion, And Order

Backlog candidates may be lightweight or mature.

A backlog candidate must have at minimum:
- a slug-based folder under `phases/backlog/`

Backlog is folder-based, not entry-file-based.
No special `README.md` file is required for a backlog candidate.
The backlog candidate meaning is carried by the files inside its slug folder.

Backlog candidate files may include:
- proposed phase-definition material
- proposed step-definition material
- shaping notes
- research
- context needed to understand the candidate

Each backlog file may contribute to a future phase or step definition.
Backlog content is allowed to stay partial and exploratory until promotion shaping makes it compliant with the promoted-phase contract.

No backlog exceptions are allowed under the target model.
A backlog folder that does not fit this folder-based candidate model must be normalized before the target model is activated.
Nested legacy structures such as `phases/backlog/<slug>/phases/...` must not survive the promotion checkpoint.

Promotion from backlog into the promoted-phases root requires:
- a fully compliant `CONTRACT.md`
- a fully compliant `WORKPLAN.md`

Promotion eligibility is based on those ready phase-governing artifacts.
Promotion execution must then materialize the full minimum promoted-phase box in the same logical checkpoint.

By the end of the promotion checkpoint, the promoted phase must contain:
- `CONTRACT.md`
- `WORKPLAN.md`
- `OPEN-ISSUES.md`
- `steps/`
- at least one `steps/stepNN-<slug>/` folder

That first step box must contain:
- `CONTRACT.md`
- `OPEN-ISSUES.md`

The phase `CONTRACT.md`, phase `WORKPLAN.md`, and first step `CONTRACT.md` must already be compatible with each other at promotion time.
The missing `OPEN-ISSUES.md` files and first step folder may either already exist inside the backlog candidate or be created atomically during the promotion checkpoint.
No phase may appear in the promoted root as a partially initialized box at the end of a checkpoint.

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
- its former promoted id is preserved in the demoted candidate content for history

If the demoted phase keeps `CONTRACT.md`, that file should preserve the former promoted id.
The preserved former promoted id uses an explicit field such as:
- `Former promoted id: phaseNNN`

If no `CONTRACT.md` is kept in the demoted backlog candidate, the demotion checkpoint must preserve that former promoted id in another backlog candidate file inside the same slug folder.

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

Every governed phase `CONTRACT.md` must also carry an explicit document-state field inside the file.
That document state owns only the contract approval state.
It does not own the runtime lifecycle state of the phase.

The required phase-contract document-state field shape is:

```md
- Document state: <draft|freeze-review-ready|frozen|retired>
```

Allowed phase-contract `Document state` values are:
- `draft`
- `freeze-review-ready`
- `frozen`
- `retired`

## Phase Workplan

`WORKPLAN.md` is created after `CONTRACT.md`.
`WORKPLAN.md` is derived from `CONTRACT.md` and cannot expand contract scope.

The minimum required field list for a phase `WORKPLAN.md` is:
- workplan document state
- phase lifecycle state
- purpose
- contract reference
- current step
- ordered implementation step list
- instantiated-step runtime state record
- step dependencies or prerequisites
- default next-step rule
- freeze-ready preparation items
- review-fix cycle items
- close-gate follow-up items
- change-control rule
- phase workplan close gate

No implementation starts until the phase workplan is frozen.
`WORKPLAN.md` is the canonical runtime-state surface for the phase.
`WORKPLAN.md` is the authority for:
- phase runtime lifecycle state
- current step
- runtime lifecycle state of each instantiated step
- step close progression and default next-step flow inside the phase
- review-fix cycle current work after freeze-gate approval

No separate phase-local status tracker is introduced for step sequencing.
Because steps do not have a step-local workplan, step runtime lifecycle state is not recorded in step `CONTRACT.md`.

### Workplan State Schema

A compliant phase `WORKPLAN.md` must contain a `## Workplan State` section before implementation work starts.
That section is the machine-readable runtime-state block for the phase.

The required fields are:
- `Workplan document state`
- `Phase lifecycle state`
- `Current step`
- `Current step type`

Allowed `Workplan document state` values are:
- `draft`
- `freeze-review-ready`
- `frozen`
- `unfrozen`
- `retired`

Allowed `Phase lifecycle state` values are:
- `in-progress`
- `freeze-ready`
- `freeze-gate-approved`
- `review-fix-cycle`
- `close-ready`
- `close-gate-approved`
- `promotion`
- `post-promotion`

Allowed `Current step type` values are:
- `implementation-step`
- `freeze-ready-preparation`
- `review-fix`
- `close-gate-follow-up`
- `idle`

`Current step` must be one of:
- an instantiated step folder path such as `steps/stepNN-<slug>`
- a freeze-ready preparation item id such as `freeze-<slug>`
- a review-fix item id such as `review-<slug>`
- a close-gate follow-up item id such as `close-<slug>`
- `none`, only when `Current step type` is `idle`

If `Current step type` is `implementation-step`, `Current step` must match an instantiated numbered step folder and a record in `## Instantiated Step Runtime`.
If `Current step type` is `freeze-ready-preparation`, `Current step` must match an item in `## Freeze-Ready Preparation`.
If `Current step type` is `review-fix`, `Current step` must match an item in `## Review-Fix Cycle`.
If `Current step type` is `close-gate-follow-up`, `Current step` must match an item in `## Close-Gate Follow-Up`.

The required field block shape is:

```md
## Workplan State

- Workplan document state: <draft|freeze-review-ready|frozen|unfrozen|retired>
- Phase lifecycle state: <in-progress|freeze-ready|freeze-gate-approved|review-fix-cycle|close-ready|close-gate-approved|promotion|post-promotion>
- Current step: <steps/stepNN-<slug>|freeze-<slug>|review-<slug>|close-<slug>|none>
- Current step type: <implementation-step|freeze-ready-preparation|review-fix|close-gate-follow-up|idle>
```

The ordered implementation step list is virtual until instantiation.
It must not assign execution numbers ahead of time.
It must contain step slugs in intended workplan order.
The list order defines default next-step flow until a step is instantiated or the workplan is unfrozen and revised.

The required ordered implementation step list shape is:

```md
## Ordered Implementation Steps

| Plan order | Step slug | Purpose | Materialized folder |
| --- | --- | --- | --- |
| 1 | <slug> | <short purpose> | <blank or steps/stepNN-<slug>> |
```

The instantiated-step runtime table records only materialized step folders.
It is keyed by the instantiated folder name.

The required instantiated-step runtime shape is:

```md
## Instantiated Step Runtime

| Step folder | Step slug | Lifecycle state | Contract path |
| --- | --- | --- | --- |
| steps/stepNN-<slug> | <slug> | <allowed lifecycle state> | steps/stepNN-<slug>/CONTRACT.md |
```

Allowed instantiated-step `Lifecycle state` values are the same lifecycle values used for phase lifecycle state.

Freeze-ready preparation and close-gate follow-up items are governed non-step current-work items.
They exist so the workplan can remain the current-work authority without inventing a separate tracker after implementation steps finish.
These items must use stable ids because `Current step` may point to them.

Allowed follow-up item states are:
- `pending`
- `in-progress`
- `complete`
- `blocked`

The required non-step follow-up shapes are:

```md
## Freeze-Ready Preparation

| Item id | State | Gate dependency | Notes |
| --- | --- | --- | --- |
| freeze-<slug> | <pending|in-progress|complete|blocked> | <dependency or none> | <notes> |

## Close-Gate Follow-Up

| Item id | State | Gate dependency | Notes |
| --- | --- | --- | --- |
| close-<slug> | <pending|in-progress|complete|blocked> | <dependency or none> | <notes> |
```

Review-fix cycle items are governed non-step current-work items.
They exist after freeze-gate approval and before close-gate follow-up.
They track review findings, review-driven fixes, required verification, and any explicit transfer out of the review-fix cycle.

Allowed review-fix item states are:
- `open`
- `in-progress`
- `fixed`
- `verified`
- `closed`
- `transferred`

The required review-fix cycle shape is:

```md
## Review-Fix Cycle

| Item id | Title | Source | Scope | State | Owner | Next action | Closure condition | Verification | Linked surface |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| review-<slug> | <short title> | <review source> | <phase|step|artifact|global> | <open|in-progress|fixed|verified|closed|transferred> | <owner> | <next action> | <testable closure condition> | <verification or none> | <step/artifact/open issue/decision or none> |
```

`review-<slug>` ids must be unique within the `## Review-Fix Cycle` section.
If a review-fix item requires implementation rework inside a step, the linked surface must point to the affected step or artifact.
If a review-fix item is transferred out of the review-fix cycle instead of closed, the linked surface must point to the receiving `OPEN-ISSUES.md` entry or other governed target.
The review-fix cycle is complete only when every review-fix item is `closed` or `transferred`.

`Current step` must be an explicit field inside `WORKPLAN.md`.
The ordered implementation step list defines the default implementation-step flow.
The ordered implementation step list is the canonical execution order.
Listed steps are virtual until they are instantiated in git.
A step becomes an official execution step only when it is instantiated as a numbered folder under the phase-local `steps/` namespace.
`Current step` may point only to an instantiated numbered step folder or to a governed non-step current-work item.
Virtual listed steps remain planned in `WORKPLAN.md` until they are instantiated.
Once a step is instantiated, its current runtime state must be recorded in the phase `WORKPLAN.md` using the governed lifecycle vocabulary in this document.

When a step is approved closed by the user, the next step defaults to the next item in the ordered implementation step list unless the user explicitly overrides it.
If that override changes the frozen workplan flow, the workplan must be unfrozen and revised, and the reason must be captured in the revision decision and in the revised `WORKPLAN.md`.

When all original implementation steps are completed, the phase does not move into a no-current-step state.
Instead, `WORKPLAN.md` transitions into freeze-ready preparation as the next current-step area until the scope is ready to ask for freeze-gate approval.

Freeze-ready preparation may be listed in a separate section of `WORKPLAN.md` so it is clear it begins after the original implementation steps are complete.
That preparation may include:
- confirming the implementation outputs are complete enough to stop execution and enter review
- preparing the agent freeze recommendation and summary for user review

When the scope is freeze ready, the next step is for the agent to suggest freeze with a summary and request CEO+CTO approval under the global freeze rule.
If the freeze gate is approved, the review-fix cycle begins.
During review-fix cycle, `WORKPLAN.md` uses the `review-fix` current step type and the `## Review-Fix Cycle` section as the current-work authority.
Routing does not point to a step folder for review-fix work unless the active review-fix item explicitly links to step rework.

After every review-fix item is `closed` or `transferred`, `WORKPLAN.md` transitions into close-gate follow-up steps as the next current-step area until phase close-gate dependencies are satisfied.

Close-gate follow-up steps may be listed in a separate section of `WORKPLAN.md` so it is clear they happen after the review-fix cycle is complete.
Those follow-up steps may include:
- resolving, addressing, or explicitly deferring remaining open issues that still block phase close
- rerunning required verification after review fixes
- completing any remaining close-gate dependencies required before close can be suggested

When all close-gate dependencies are satisfied, the next step is for the agent to suggest close with a summary and request the required close-gate approval.
If the user rejects either the freeze suggestion or the close suggestion and asks for further work that changes the frozen workplan flow, that rejection triggers a quick workplan unfreeze, revision, and re-freeze before execution continues.

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
- changing the execution order of an instantiated step, but only by making it lose its number and updating the related phase `OPEN-ISSUES.md` entry in the same checkpoint
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

Every governed step `CONTRACT.md` must also carry an explicit document-state field inside the file.
That document state owns only the step-contract approval state.
Step runtime lifecycle state is recorded in the phase `WORKPLAN.md`, not in the step `CONTRACT.md`.

The required step-contract document-state field shape is:

```md
- Document state: <draft|freeze-review-ready|frozen|retired>
```

Allowed step-contract `Document state` values are:
- `draft`
- `freeze-review-ready`
- `frozen`
- `retired`

The exact required file inventory inside a step folder is:
- `CONTRACT.md`
- `OPEN-ISSUES.md`

A listed workplan step is virtual until instantiation.

Substeps are allowed only as local descriptive planning inside a step.
They are not a governed routing layer, they do not receive folders, and they do not own lifecycle state, promotion, numbering, or close gates.
If a substep needs its own contract, gate, artifacts, or user approval, it must be promoted into a real governed step.
Review-fix items are not substeps; they are governed runtime items in the phase `WORKPLAN.md`.

All step folders live under the phase-local `steps/` namespace.
Official instantiated step folders use `steps/stepNN-<slug>/`.
Preserved former-step folders use `steps/<slug>/`.
Step slugs must be unique within a phase.
The `steps/` namespace isolates step slugs from phase-root governed files and folders.
This resolves the review finding that former-step re-instantiation could misidentify or collide with phase-root folders.

Step instantiation rule:
- when a step is selected for official execution, it receives the current execution number from `WORKPLAN.md`
- before creating a new numbered step folder, the phase must check whether a preserved former-step folder with the same slug already exists under `steps/`
- if a matching preserved former-step folder exists, it must be re-instantiated by renaming it to `steps/stepNN-<slug>/`
- that same re-instantiation checkpoint must update its `CONTRACT.md` if needed to match the current frozen phase contract and workplan
- that same re-instantiation checkpoint must also update the related phase `OPEN-ISSUES.md` entry so the former-step / orphan record is removed or closed
- if no matching preserved former-step folder exists, create a new `steps/stepNN-<slug>/` folder with the required files

Step order-change rule:
- if an instantiated step's execution order is changed, it loses its step number and stops being an official execution step
- that preserved former-step folder keeps only the original slug under `steps/`
- the same checkpoint must create or update a phase `OPEN-ISSUES.md` entry that points to that preserved folder and records that it is a former step awaiting disposition
- when that work is later selected again for execution, it receives the actual current execution number at re-instantiation time
- no numbered step folder may remain if its number no longer matches execution order in practice

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
- `phases/phaseNNN-<slug>/steps/stepNN-<slug>/OPEN-ISSUES.md`

Only `OPEN-ISSUES.md` is required locally at this stage.
Local `STATUS.md` is not introduced at the phase or step layer.
Local `HANDOFF.md` is optional continuity support only.

Local open issues should be resolved locally by default at the step or phase level.
If a local open issue cannot be resolved locally, it may be explicitly deferred upward to the global `OPEN-ISSUES.md`.

`OPEN-ISSUES.md` is a current-state surface, not a narrative history ledger.
`OPEN-ISSUES.md` records scoped unresolved blockers, transfers, and explicit dispositions only.
It does not own current step, document approval state, or lifecycle state.
Audit trail for open-issue creation, closure, and transfer is provided by git checkpoints tied to the related repo-truth change.
An empty `OPEN-ISSUES.md` means only that no issues are currently open at that scope.
It does not itself distinguish whether no issue was ever found, all issues were resolved locally, or issues were transferred upward.

### Open Issue Entry Contract

This contract resolves the review finding that `OPEN-ISSUES.md` was not yet script-ready or contextless-agent-ready at the item level.

The contract is lean, artifact-agnostic, and file-friendly.
It does not introduce issue IDs.
The entry title is the human handle.
Stable IDs may be added later only if cross-file automation, reopening, duplicate tracking, or other real needs prove that titles plus git history are insufficient.

An open issue entry preserves one unresolved reality gap so another person or agent can:
1. understand it
2. trust that it is real
3. know why it matters
4. know what to do next
5. know what would close it

One entry equals one unresolved reality gap.
Do not mix facts and guesses.
Observed behavior and expected behavior are both mandatory.
Evidence is mandatory.
Impact is mandatory.
Next action must be actionable.
Closure condition must be testable.
If exact location is unknown, say that explicitly instead of faking precision.

Required fields:
- `Title`
- `Affected artifact or surface`
- `Exact location`
- `Observed behavior`
- `Expected behavior`
- `Evidence`
- `Impact`
- `Owner`
- `Next action`
- `Closure condition`
- `Last updated`
- `Source session`

`Title` answers what the unresolved issue is.
It must be short, specific, and searchable.
It names the issue, not the solution.

`Affected artifact or surface` and `Exact location` answer where the issue lives.
Valid locations include:
- code file plus method plus line range
- document file plus section or heading
- workflow
- route
- screen
- API
- schema
- config
- test

`Observed behavior` answers what current reality shows.
It must describe actual current reality concretely, not interpretation.

`Expected behavior` answers what should be true instead.
It is the comparison point for the issue.

`Evidence` answers how we know the issue is real.
Valid evidence includes:
- log excerpt
- screenshot
- failing test
- reproduction note
- file reference
- line reference
- commit reference
- quoted text from a document
- exact contradiction between artifacts

Evidence must be concrete.
`Seems wrong` is not evidence.

`Impact` answers why the issue matters.
Valid impacts include:
- wrong behavior
- ambiguity
- broken contract
- user risk
- review risk
- implementation risk
- operational risk
- maintainability risk
- traceability gap

Impact must explain consequence, not just restate the issue.

`Owner` answers who moves the issue next.
The owner may be an owning scope or responsible actor, not necessarily a person.
Examples include:
- `step`
- `phase`
- `global`
- `user`
- `agent`
- `script-governance`

There must be one clear owner.
Even if others help, one owner is responsible for movement.

`Next action` answers the next concrete move.
It must be specific enough that someone can start immediately.
Valid examples include:
- investigate contradiction
- update contract wording
- verify route behavior
- add missing evidence
- decide canonical source

`Closure condition` answers what must become true to close the issue.
It must be testable or checkable.
It should describe the required outcome, not vague intent.
If needed, include how closure will be verified.

`Last updated` records when the entry was last meaningfully touched.
It must include a date and the reason for the update.
Use meaningful updates, not cosmetic edits.

`Source session` records the agent session UUID or `none`.
If an agent creates or materially updates an open issue and the current session UUID is available, it must record that UUID.
This supports deeper audit by letting a future reviewer locate the originating discussion when an issue is unclear.
It does not replace evidence and does not become the primary issue identity.

Optional fields may be added only when they carry real value:
- `Status`, only if the open-issues list needs distinctions such as `new`, `investigating`, `blocked`, `waiting`, or `ready`
- `Unknowns`, only if uncertainty itself is important
- `Hypothesis`, only if it helps investigation and is clearly marked as hypothesis, not fact
- `Blocked by`, only when there is a real dependency
- `Transferred from`, only when the issue moved from step to phase or phase to global

Avoid these fields for now because the best part is no part:
- issue ID
- priority or severity, unless the process actively uses them
- root cause, unless already known and relevant
- proposed solution, unless it is the next action
- long history notes that version control already captures

The lean entry template is:

```md
## <short, specific, searchable title>

- Title: <same as heading or precise display title>
- Affected artifact or surface: <artifact or surface>
- Exact location: <specific location or unknown>
- Observed behavior: <current reality>
- Expected behavior: <desired/correct reality>
- Evidence: <concrete evidence>
- Impact: <consequence>
- Owner: <owning scope or responsible actor>
- Next action: <specific next move>
- Closure condition: <testable outcome>
- Last updated: <YYYY-MM-DD - reason>
- Source session: <agent session UUID or none>
```

Global open issues act as the intake pool for deferred future work, but they are not the same thing as backlog phase candidates.
`phases/backlog/` holds explicit future phase candidates, not every deferred global open issue.
Promotion from a global open issue into `phases/backlog/<slug>/` is an explicit shaping step, not an automatic move.

During transition, the bootstrap global `context/OPEN-ISSUES.md` may still contain items that should become phase-local after promotion.
The phase-model promotion checkpoint must explicitly triage that file.
Foundation-scoped items must be moved into `phases/phase0-foundation/OPEN-ISSUES.md`.
Only true global/bootstrap items may remain in `context/OPEN-ISSUES.md` after that triage.
The triage and any moved items must be committed in the same logical checkpoint so git preserves the transfer audit trail.

A step cannot close while it still owns unresolved step-scoped open items unless those items are explicitly transferred forward.
A phase cannot close while it still owns unresolved phase-scoped open items.
To close a phase, remaining phase-scoped items must be either resolved or transferred out to backlog or general-level open items.

Preserved former-step folders are phase-scoped unresolved items.
They must be tracked in the phase `OPEN-ISSUES.md` until they are re-instantiated, explicitly deferred upward, or explicitly accepted as no longer needed under the phase contract and user approval.
When a preserved former-step folder is re-instantiated, the matching phase `OPEN-ISSUES.md` entry must be updated or removed in the same checkpoint.
No phase may close while a preserved former-step folder still exists without an explicit recorded disposition.

Open-issues commit rule:
- every meaningful `OPEN-ISSUES.md` update must be committed in the same logical checkpoint as the event it records
- do not leave an open-issue creation, closure, transfer, or final-clear state sitting uncommitted across later unrelated work
- when the last open issue at a scope is resolved or transferred out, the resulting empty `OPEN-ISSUES.md` state must be part of that same checkpoint so git preserves how the scope became clear
- `OPEN-ISSUES.md` does not need a separate dedicated commit if the related repo-truth change is already part of the same logical checkpoint

## Handoff

`HANDOFF.md` is optional and local in the target phase model.
It is not a boxed truth surface.
It is a continuity aid only.

Allowed local handoff locations are:
- `phases/phaseNNN-<slug>/HANDOFF.md`
- `phases/phaseNNN-<slug>/steps/stepNN-<slug>/HANDOFF.md`

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
Global `context/STATUS.md` is also part of the foundation-bootstrap runtime only and not part of the target phase execution model after promotion.

## Artifacts

The required file inventory inside a promoted phase folder is:
- `CONTRACT.md`
- `WORKPLAN.md`
- `OPEN-ISSUES.md`
- `steps/`
- one or more `steps/stepNN-<slug>/` folders

That inventory is not optional after promotion.
If promotion is executed, the full promoted-phase inventory must exist by the end of the same logical checkpoint.

Artifacts are authored only inside steps.
The phase does not create draft artifacts of its own.
The phase collects approved step outputs and is the only scope that may promote those collected artifacts toward canonical repo truth.

Artifact storage is boxed as:
- step `drafts/`
- phase `artifacts/`
- canonical repo destinations outside the active phase only after phase promotion

`drafts/` is optional inside a step and is created only when that step needs to author draft outputs.
`artifacts/` is optional at phase scope and is created only when the phase first collects approved step outputs.

Step draft artifacts are stored under `steps/stepNN-<slug>/drafts/`.
The step contract must define:
- which draft outputs are promotable to phase scope
- any conditions that must be satisfied before those outputs may be collected by the phase

When a step closes, the phase scope executes step promotion under the step contract promotion rule.
Approved step outputs move from `steps/stepNN-<slug>/drafts/` into the phase-root `artifacts/` folder.
Step promotion to phase artifacts is mechanical after step close because collected artifacts remain isolated inside the active phase.
Step promotion does not by itself promote artifacts to canonical repo truth.

`phases/phaseNNN-<slug>/artifacts/` holds collected phase-owned artifacts while the phase is still active.
Those artifacts remain isolated inside the phase until phase promotion.

When a phase closes, the phase scope executes phase promotion under the phase contract artifact collection and promotion rule.
Selected collected artifacts move from the phase-root `artifacts/` folder to the canonical repo locations named by the phase contract.
Moving collected phase artifacts into canonical repo locations requires artifact-freeze approval under the global freeze rule.
That CEO+CTO artifact-freeze approval must be recorded before canonical artifact movement, either as part of the phase close gate or as a prior explicit artifact-freeze approval.
If the required artifact-freeze approval is already recorded, canonical artifact movement remains a mechanical promotion step after close approval.

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

Freeze gate approval requires CEO+CTO approval under the global freeze rule.
Close gate approval requires explicit user approval.
If close approval also authorizes canonical artifact promotion, that close approval must include CEO+CTO artifact-freeze approval under the global freeze rule.
If canonical artifact-freeze approval was already recorded before close, close approval may remain a separate explicit user approval and promotion stays mechanical after close.

If the freeze gate is approved:
- execution for that scope is frozen for review
- the review-fix cycle begins
- the scope remains open

A phase is close ready when:
- every review-fix item is `closed` or explicitly `transferred`
- review findings are addressed through the governed `## Review-Fix Cycle` section
- verification is rerun as required
- close-gate dependencies are satisfied
- no unresolved phase-scoped open items remain unless they are explicitly transferred out under the phase rules

A step is close ready when:
- every review-fix item affecting that step is `closed` or explicitly `transferred`
- review findings are addressed through the governed `## Review-Fix Cycle` section
- verification is rerun as required
- close-gate dependencies are satisfied
- no unresolved step-scoped open items remain unless they are explicitly transferred forward under the step rules

If the close gate is approved:
- the scope closes
- promotion runs next as a mechanical transition
- promotion is not a separate approval gate
- any canonical artifact movement during promotion is allowed only after the required CEO+CTO artifact-freeze approval is already recorded

Promotion execution is owned by the phase scope because the phase workplan owns completion flow.

For step close and promotion:
- the phase scope executes step promotion under the step contract promotion rule
- the phase scope updates the phase workplan and any affected phase-local files in the same logical checkpoint
- after step promotion, control returns to phase scope for the next current step

For phase close and promotion:
- the phase scope executes phase promotion
- the phase moves to `phases/complete/` with the number it closed under
- completion may also move outputs to other destinations if that is defined in the phase contract
- canonical artifact outputs may move only if their artifact-freeze approval under the global freeze rule is already recorded
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

Document approval state and scope lifecycle state are separate concepts.
A contract or workplan being frozen or approved does not by itself mean the related step or phase is freeze ready, freeze-gate approved, close ready, or close-gate approved.
A step or phase reaching one of those lifecycle states does not by itself re-approve the underlying contract or workplan.

Approval-state ownership is:
- phase `CONTRACT.md` owns phase-contract document approval state
- step `CONTRACT.md` owns step-contract document approval state
- phase `WORKPLAN.md` owns phase-workplan document approval state
- phase `WORKPLAN.md` owns phase runtime lifecycle state
- phase `WORKPLAN.md` owns step runtime lifecycle state for instantiated steps
- scope `OPEN-ISSUES.md` owns unresolved blockers, transfers, and explicit dispositions only
- a global decision file owns only broader repo-truth approvals that the decision rules require to be preserved as frozen decisions

The lifecycle states in this section are scope-lifecycle states.
For a phase, they are recorded in the phase `WORKPLAN.md`.
For a step, they are also recorded in the phase `WORKPLAN.md` because no step-local `WORKPLAN.md` exists.

Approval is recorded as follows:
- document approval in the file being approved, by changing its required document-state field
- scope-lifecycle approval in the governing phase `WORKPLAN.md`
- blocker/open-item status in the relevant scope `OPEN-ISSUES.md`
- broader repo-truth approval in a global decision file when the decision rules require it
- artifact-freeze approval for canonical promotion in the phase `WORKPLAN.md`, the phase workplan close-gate record, or a global decision file, as required by the active governance rule

For contracts and workplans:
- the approved file must explicitly say it is frozen or approved
- if a workplan is re-frozen after unfreeze, that state change must be recorded in the workplan itself

For step and phase closure:
- closure approval must be reflected in the governing workplan and any affected `OPEN-ISSUES.md`
- if closure causes promotion, the related artifact or folder move must be part of the same logical checkpoint
- if closure causes canonical artifact promotion, that checkpoint must also include the recorded CEO+CTO artifact-freeze approval or point to the prior recorded approval that authorizes the move

For next-phase selection and renumbering:
- routing updates, folder renames, and reference updates caused by the reviewed selection order must be part of the same logical checkpoint
- do not leave promoted-phase numbering and routing partially updated across checkpoints

For decisions:
- decision approval is recorded in the decision file under `APPROVAL`
- the matching `context/decisions/INDEX.md` update must be part of the same checkpoint

Each approval that changes repo truth must end in a commit.
That commit must include all files needed to make the approved state self-consistent.

Current truth is reconstructed from the boxed current-state files.
Audit trail is reconstructed from git checkpoints that update those files.
No separate narrative progress ledger is introduced at this stage.

## Decision Carry-Through

Approved decisions must be carried through before a phase-model item may be described as integrated, fixed, closed, or implemented.

For this phase-model artifact, carry-through requires checking and updating every affected:
- requirement section
- schema or field contract
- routing rule
- gate rule
- transition rule
- decision file
- example or template
- live bootstrap status or handoff reference, if the live transition surface mentions the item

If an affected surface is intentionally left unchanged, the reason must be recorded in the same logical checkpoint.

The carry-through check must happen before commit.
The commit must include every dependent update needed to keep the repo truth self-consistent.

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
