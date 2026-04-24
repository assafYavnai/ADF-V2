# BOXED-MODEL-BUILDER-REVIEWER-PIPELINE

## CONTEXT

While reviewing the phase-model demotion finding, the discussion stepped back from the symptom and re-examined actual day-to-day ADF usage.
The user clarified that a phase starts from a vague need or pain and matures into a high-level requirement list, a contract, a workplan, and then concrete steps.
The workplan is an educated execution hypothesis, and implementation may reveal gaps that require revisiting the plan.

The discussion then generalized this beyond phases.
The same boxed model should govern ADF as a whole.
Each box should eventually be scriptable as a process with explicit inputs and outputs.

## OPTIONS

- Treat phase and step files as static documents and add ad hoc governance around them later.
- Treat each box as a governed builder process that consumes an input, validates maturity, and produces the next artifact.
- Treat review and testing as separate later additions rather than part of the box-to-box maturity model.

## DECISION

ADF uses a boxed builder-reviewer model.

A governed box is a process boundary with:
- input artifacts or inputs
- rules
- an output artifact
- a maturity check
- a failure path
- promotion or handoff behavior

Each builder box is also a reviewer of the previous box.
The builder must validate that the input artifact is mature enough to create the requested output.
If the input is not mature enough, the builder must return a specific gap to the owning upstream box instead of inventing missing truth or bypassing governance.

The default pipeline pattern is:
- need or pain becomes a definition input
- a builder creates the next governed artifact
- that builder validates the maturity of the previous artifact
- if validation fails, work returns to the previous box for revision
- if validation passes, the output artifact can move to its next governed box

For the phase model, the concrete use case is:
- phase need or pain goes into a phase contract builder
- phase contract builder outputs phase `CONTRACT.md`
- phase workplan builder consumes phase `CONTRACT.md`, reviews whether it is mature enough to plan from, and outputs phase `WORKPLAN.md`
- step builder consumes the selected workplan step intent, reviews whether the workplan supplies enough context, and outputs step `CONTRACT.md`
- step instantiation consumes step `CONTRACT.md` and phase `WORKPLAN.md`, then creates or reuses the step folder under `steps/`
- implementation, review, test, gate, and promotion boxes consume those artifacts and validate the previous outputs before advancing

Discovery during implementation is expected governance input.
If implementation reveals that the current workplan is incomplete but the work remains inside the phase contract, the workplan returns to governed change control.
If the gap does not fit the phase contract, the work must not be absorbed by the workplan and must move to the appropriate backlog or open-issue path.

Future scripts should implement these boxes with explicit inputs and outputs.
Scripts may enforce the frozen boxed model but must not redefine it.

## APPROVAL

EXPLICIT
