# PHASE-MODEL-WORKPLAN-CURRENT-STEP-AND-CLOSE-GATE-FLOW

## CONTEXT

The review of `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` raised a pushback that the draft did not yet define a canonical active-step tracker clearly enough.
The draft already said that routing must not manage step sequencing and that no separate local status tracker should be introduced, but it still left too much room for agents or scripts to invent how current step and close-gate flow should be inferred.

## PUSHBACK

The core pushback was:
- the draft still did not say explicitly enough where the current step is recorded
- saying that the current step is only deducible from the step list was wrong because the agreed model already keeps current step inside `WORKPLAN.md`
- saying that all steps closed means no current step is selected was also wrong because the phase should transition into close-gate handling, not into an empty state
- if freeze is suggested and the user rejects, the model still needs a governed way to resume work without bypassing the workplan authority

## DISCUSSION SUMMARY

The discussion returned to the earlier agreement that the best state surface is the one that already exists.
The user explicitly restated that current step belongs in `WORKPLAN.md`, and that if the workplan can already hold it there is no reason to invent another mechanism.

The discussion then clarified the relation between current step and next-step flow.
Current step is an explicit field in the workplan.
Default next-step flow is derived from the ordered implementation step list.
If the user changes that frozen flow, the workplan must be unfrozen and revised, with the reason captured in the revision decision and the revised workplan.

The discussion also clarified post-implementation behavior.
After the original implementation steps are complete, the phase does not enter a no-current-step state.
Instead, the workplan transitions into governed non-step current-work items.
A later lifecycle-sequencing clarification split those items into freeze-ready preparation before review and close-gate follow-up after the review-fix cycle.
Freeze-ready preparation includes the agent freeze recommendation step.
Close-gate follow-up includes remaining open-issue handling, rerun verification after review fixes, remaining close-gate dependencies, and the agent close recommendation step.

Finally, the discussion clarified what happens if the agent suggests freeze and the user rejects it.
That rejection must trigger a quick workplan unfreeze, revision, and re-freeze before execution continues, so the workplan remains the authority.

## OPTIONS

- Add a separate tracker for current step outside `WORKPLAN.md`.
- Treat current step as only deducible from the ordered step list.
- Keep current step as an explicit field inside `WORKPLAN.md` and keep default next-step flow in the ordered implementation step list.
- Let the phase move into a no-current-step state after implementation steps are complete.
- Keep post-implementation freeze-ready preparation and close-gate follow-up work inside `WORKPLAN.md`.

## DECISION

The agreed target phase-model rules are:

- `WORKPLAN.md` is the authority for current step and default next-step flow inside the phase
- `Current step` must be an explicit field in phase `WORKPLAN.md`
- `Current step` is recorded in the required `## Workplan State` section
- `Current step type` is recorded beside it and may be only `implementation-step`, `freeze-ready-preparation`, `close-gate-follow-up`, or `idle`
- the ordered implementation step list defines the default implementation-step flow
- the ordered implementation step list is virtual until instantiation and must not assign execution numbers ahead of time
- routing does not decide current step
- a step is selected for routing purposes only when the workplan `Current step` field points to an instantiated step folder under `steps/`
- non-step current work may be selected only when `Current step` points to a stable item id in `## Freeze-Ready Preparation` or `## Close-Gate Follow-Up`

- when a step is approved closed by the user, the next step defaults to the next item in the ordered implementation step list unless the user explicitly overrides it
- if that override changes the frozen workplan flow, `WORKPLAN.md` must be unfrozen and revised
- the reason for that revision must be captured in the revision decision and in the revised `WORKPLAN.md`

- after the original implementation steps are complete, the phase does not move into a no-current-step state
- instead, the workplan transitions into freeze-ready preparation as the next current-step area
- freeze-ready preparation items may be listed in a separate section of `WORKPLAN.md`
- freeze-ready preparation items must use stable `freeze-<slug>` ids when they can be referenced by `Current step`
- freeze-ready preparation includes confirming implementation outputs and preparing the agent freeze recommendation and summary
- after the freeze gate is approved and the review-fix cycle is complete, the workplan transitions into close-gate follow-up steps as the next current-step area
- close-gate follow-up steps may be listed in a separate section of `WORKPLAN.md`
- close-gate follow-up items must use stable `close-<slug>` ids when they can be referenced by `Current step`
- those follow-up steps may include:
  - resolving, addressing, or explicitly deferring remaining open issues that still block phase close
  - rerunning required verification after review fixes
  - completing any remaining close-gate dependencies required before close can be suggested
  - preparing the agent close recommendation and summary for user review

- when all freeze-ready preparation dependencies are satisfied, the next step is for the agent to suggest freeze with a summary and for the user to either approve or reject
- when all close-gate dependencies are satisfied, the next step is for the agent to suggest close with a summary and for the user to either approve or reject
- if the user rejects and asks for further work that changes the frozen workplan flow, that rejection triggers a quick workplan unfreeze, revision, and re-freeze before execution continues

This decision clarifies the workplan authority model and closes the active-step-tracker ambiguity without introducing a new tracker surface.

## APPROVAL

EXPLICIT
