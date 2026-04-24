# PHASE-MODEL-FREEZE-READY-PRECEDES-CLOSE-READY

## CONTEXT

The second review pass on `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` found that the draft still carried one lifecycle contradiction.
The workplan section still implied that close-gate dependencies had to be satisfied before freeze could be suggested, while the already approved two-gate lifecycle said freeze approval begins the review-fix cycle and close-ready comes later.

## OPTIONS

- Leave the workplan wording as-is and let agents or scripts infer which lifecycle section wins.
- Rewrite the workplan wording so freeze suggestion happens at freeze-ready, then review-fix runs, then close-gate follow-up leads to close-ready.
- Collapse freeze and close back into one gate.

## DECISION

The agreed target phase-model rules are:

- freeze-ready preparation happens before the freeze gate, not after close-gate dependency completion
- when the original implementation steps are complete, `WORKPLAN.md` transitions into freeze-ready preparation as the next current-step area
- when the scope is freeze ready, the next step is for the agent to suggest freeze with a summary and for the user to either approve or reject
- if the freeze gate is approved, the review-fix cycle begins
- during review-fix cycle, `WORKPLAN.md` uses `## Review-Fix Cycle` and `review-<slug>` item ids as the current-work authority
- after every review-fix item is `closed` or `transferred`, `WORKPLAN.md` transitions into close-gate follow-up steps as the next current-step area
- close-gate follow-up work may include remaining open-issue handling, rerun verification after review fixes, and any remaining close-gate dependencies required before close can be suggested
- when all close-gate dependencies are satisfied, the next step is for the agent to suggest close with a summary and for the user to either approve or reject
- if the user rejects either the freeze suggestion or the close suggestion and asks for further work that changes the frozen workplan flow, `WORKPLAN.md` must be unfrozen, revised, and re-frozen before execution continues

This decision supersedes only the conflicting lifecycle-sequencing wording in `context/decisions/PHASE-MODEL-WORKPLAN-CURRENT-STEP-AND-CLOSE-GATE-FLOW.md`.
That earlier decision remains valid for the rules that `WORKPLAN.md` owns `Current step`, routing does not manage step sequencing, and the phase does not move into a no-current-step state after the original implementation steps are complete.

## APPROVAL

EXPLICIT
