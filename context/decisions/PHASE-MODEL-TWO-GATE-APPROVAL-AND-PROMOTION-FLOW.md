# PHASE-MODEL-TWO-GATE-APPROVAL-AND-PROMOTION-FLOW

## CONTEXT

The review of `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` raised a pushback that the approval and close-gate flow was still underspecified.
The draft distinguished freeze-review readiness, freeze approval, phase close gate, and movement to `phases/complete/`, but it did not yet state one exact transition order or one exact ownership model for promotion and routing updates.

## PUSHBACK

The core pushback was:
- the draft still did not state clearly enough whether freeze approval and close approval were separate events
- the draft still did not state clearly enough when promotion happens
- the draft still did not state clearly enough who is responsible for promotion
- phase close and next-phase selection had already been separated, but the draft still needed the exact order that comes between review completion and movement to `phases/complete/`

The related discussion added two further requirements:
- after promotion, control returns to the higher scope
- the phase is responsible for updating `phases/ROUTING.md`

## DISCUSSION SUMMARY

The discussion widened the approval model into two gates.
The agreed model is not a single close approval.
Instead, work first becomes ready for review, then enters a review-fix cycle, then becomes ready to close.

The agreed order is:
- in progress
- freeze ready
- freeze gate approved
- review-fix cycle
- close ready
- close gate approved
- promotion
- post-promotion state

The discussion also clarified promotion ownership.
Promotion is not a separate approval gate.
It is a mechanical step that runs after close-gate approval.
Because the phase workplan owns completion flow, promotion execution is owned by the phase scope.
Later review clarified that mechanical promotion does not weaken the global freeze rule.
Freeze gates require CEO+CTO approval under the global freeze rule.
Canonical artifact movement during phase promotion is allowed only after CEO+CTO artifact-freeze approval is recorded.

That means:
- a step does not promote itself in isolation
- the phase scope promotes the step under the step contract promotion rule
- the phase scope also promotes the phase itself when phase close is approved
- the phase scope is responsible for updating `phases/ROUTING.md` as part of the phase-promotion checkpoint

The discussion also clarified post-promotion behavior.
After phase promotion, the system may be idle until new input arrives.
For now, only explicit user input exits that idle state.
Future script governance may define additional triggers later.

## OPTIONS

- Keep freeze review, close gate, and promotion loosely described and let later agents/scripts infer the exact order.
- Collapse freeze and close into one approval event.
- Use a two-gate model where freeze approval starts review, close approval ends the scope, and promotion runs after close as a mechanical phase-owned step.

## DECISION

The agreed target phase-model rules are:

- a step or phase moves through these states in order:
  - in progress
  - freeze ready
  - freeze gate approved
  - review-fix cycle
  - close ready
  - close gate approved
  - promotion
  - post-promotion state

- `freeze ready` is the ready-for-review state
- `freeze ready` means the scope is ready to ask for freeze-gate approval and begin the review-fix cycle
- `freeze ready` does not itself close the scope

- freeze gate approval requires CEO+CTO approval under the global freeze rule
- close gate approval requires explicit user approval
- if close approval also authorizes canonical artifact promotion, that close approval must include CEO+CTO artifact-freeze approval under the global freeze rule
- if canonical artifact-freeze approval was already recorded before close, close approval may remain a separate explicit user approval

- if the freeze gate is approved:
  - execution for that scope is frozen for review
  - the review-fix cycle begins
  - `WORKPLAN.md` records review-fix current work in `## Review-Fix Cycle`
  - the scope remains open

- `close ready` means:
  - every review-fix item is `closed` or `transferred`
  - review findings are addressed through the governed `## Review-Fix Cycle` section
  - verification is rerun as required
  - close-gate dependencies are satisfied
  - scope-specific open-issue rules for closure are satisfied

- if the close gate is approved:
  - the scope closes
  - promotion runs next as a mechanical transition
  - promotion is not a separate approval gate
  - canonical artifact movement is allowed only after the required CEO+CTO artifact-freeze approval is already recorded

- promotion execution is owned by the phase scope because the phase workplan owns completion flow

- for step close and promotion:
  - the phase scope executes step promotion under the step contract promotion rule
  - step promotion to phase artifacts remains mechanical because artifacts remain isolated inside the active phase
  - the phase scope updates the phase workplan and any affected phase-local files in the same logical checkpoint
  - after step promotion, control returns to phase scope for the next current step

- for phase close and promotion:
  - the phase scope executes phase promotion
  - the phase moves to `phases/complete/` with the number it closed under
  - canonical artifact outputs may move only if their artifact-freeze approval under the global freeze rule is already recorded
  - the phase scope updates `phases/ROUTING.md` in the same logical checkpoint
  - after phase promotion, routing either points to the selected next active phase or explicitly says that no active phase is selected and the system is idle / waiting for input

- next-phase selection remains separate from phase close and phase promotion
- for now, only explicit user input exits the idle routing state
- future script governance may define additional governed triggers

This decision defines the approval order, promotion responsibility, and post-promotion routing behavior for the target phase model.

## APPROVAL

EXPLICIT
