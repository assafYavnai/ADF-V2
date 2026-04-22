# PHASE-MODEL-SEPARATES-DOCUMENT-APPROVAL-FROM-RUNTIME-STATE

## CONTEXT

The remaining structural review issue on the phase-model draft was approval-state determinism.
The draft already defined the lifecycle order and the two-gate model, but it still left too much room for different agents or future scripts to record the same approval state in different places.
The discussion then narrowed the model by first principles:
- document approval and scope lifecycle are different kinds of state
- no new tracker file should be introduced
- the phase `WORKPLAN.md` should own runtime state
- step `CONTRACT.md` should stay a scope-definition file rather than becoming a second runtime tracker
- `OPEN-ISSUES.md` should stay blocker-only
- decision files should be used only when broader repo truth requires frozen decision preservation

## OPTIONS

- Keep the generic approval wording and let agents or scripts choose where to record approval and lifecycle state.
- Add a new local status-style tracker for runtime approval state.
- Separate document approval from scope lifecycle and make the phase `WORKPLAN.md` the canonical runtime-state owner while keeping contracts and open-issues files narrowly boxed.

## DECISION

The agreed target phase-model rules are:

- document approval state and scope lifecycle state are separate concepts
- phase `CONTRACT.md` owns only phase-contract document approval state
- step `CONTRACT.md` owns only step-contract document approval state
- phase `WORKPLAN.md` owns phase-workplan document approval state
- phase and step `CONTRACT.md` files must serialize document approval state with `Document state: <draft|freeze-review-ready|frozen|retired>`
- phase `WORKPLAN.md` is the canonical runtime-state surface for the phase
- phase `WORKPLAN.md` owns:
  - phase runtime lifecycle state
  - current step
  - runtime lifecycle state of each instantiated step
  - step close progression and next-step flow
- phase `WORKPLAN.md` must serialize that runtime state through the required `## Workplan State`, `## Ordered Implementation Steps`, `## Instantiated Step Runtime`, `## Freeze-Ready Preparation`, and `## Close-Gate Follow-Up` sections defined in the phase-model artifact
- phase `WORKPLAN.md` must serialize workplan document approval state with `Workplan document state: <draft|freeze-review-ready|frozen|unfrozen|retired>`
- allowed phase and step lifecycle-state values are `in-progress`, `freeze-ready`, `freeze-gate-approved`, `review-fix-cycle`, `close-ready`, `close-gate-approved`, `promotion`, and `post-promotion`
- `Current step type` may be only `implementation-step`, `freeze-ready-preparation`, `close-gate-follow-up`, or `idle`
- because no step-local `WORKPLAN.md` exists, step runtime lifecycle state is recorded in the phase `WORKPLAN.md`, not in the step `CONTRACT.md`
- `OPEN-ISSUES.md` records scoped unresolved blockers, transfers, and explicit dispositions only
- `OPEN-ISSUES.md` must not own current step, document approval state, or lifecycle state
- global decision files are used only for broader repo-truth approvals that the decision rules require to be preserved as frozen decisions
- current truth is reconstructed from the boxed current-state files
- audit trail is reconstructed from git checkpoints that update those files
- no separate narrative progress ledger is introduced at this stage

This decision closes the approval-state determinism gap without adding a new tracker layer.

## APPROVAL

EXPLICIT
