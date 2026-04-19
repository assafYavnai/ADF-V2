# HANDOFF

Status: ACTIVE

## Current state

ADF-V2 is a new clean repository.
The foundation layer is still being defined.
`CONTEXT.md` is now frozen.
`phases/phase0-foundation/README.md` is now frozen.

## Current task

Review the phase model draft in `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` as the current active Foundation Step 1 surface.

## Current step

Foundation Step 1 - phase model review draft

## Session summary

This repository is still building the foundation framework itself.
The current discussion is defining how context works, how files should be shaped, and how agents should preserve continuity without hidden assumptions.
The root bootstrap files now exist, and `AGENTS.md` routes agents through the foundation workplan, foundation readme, context files, and rules before substantive work.
The explicit decisions from this discussion are now saved under `context/decisions/`.
For handoff, the next agent must read the curated decision list below rather than trying to infer truth from the full decisions folder.
The `CONTEXT.md` contract gaps found during review were addressed in this session so the draft now matches actual repo practice more closely.
The naming-rule scope and open-issue closure rule were tightened again in this session to remove the last remaining governance ambiguities.
`CONTEXT.md` was then explicitly approved, frozen, and promoted in place.
`phases/phase0-foundation/README.md` was then rewritten to match the live foundation contract and the mandatory future-alignment requirement around CEO / CTO / DEV.
`phases/phase0-foundation/README.md` was then explicitly approved, frozen, and promoted in place.
The foundation work model was then clarified so the gate is a post-freeze check, not a step, and freeze was made explicit as a global CEO+CTO approval rule.
Additional deferred foundation concerns were then captured in `OPEN-ISSUES.md` so they stay visible without widening the current active step.
A first draft artifact for high-level phase-model requirements was then created under `context/artifacts/` so the ongoing discussion can keep agreed items, open questions, and later-deferred items separate without freezing phase truth too early.
The lower-level operational mechanics were then defined so the phase-model draft no longer carries open model holes.
That draft was then rewritten into a review-ready canonical form while still remaining an unfrozen artifact.
Reviewer pushback on decision routing and handoff governance was then addressed in the draft.
The draft now makes `WORKPLAN.md` the owner of current and next step inside a phase, defines `context/decisions/INDEX.md` as the target curated decision-read surface, and constrains `HANDOFF.md` to optional local continuity-only use in the target model.
That transition rule and local-handoff governance were then saved as an explicit decision so later agents do not have to reconstruct the reasoning from memory.

## Session pointers

- `phases/phase0-foundation/WORKPLAN.md`
- `phases/phase0-foundation/README.md`
- `CONTEXT.md`
- `RULES.md`
- `AGENTS.md`
- `CLAUDE.md`
- `GEMINI.md`
- `context/STATUS.md`
- `context/OPEN-ISSUES.md`
- `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md`

## Required decision files for this handoff

- `context/decisions/FOUNDATION-SCOPE-AND-OLD-WORK-BOUNDARY.md`
- `context/decisions/FOUNDATION-WORKPLAN-AND-APPROVAL-GATE.md`
- `context/decisions/MANUAL-CONTEXT-STRUCTURE-AND-TRACKERS.md`
- `context/decisions/NAMING-AND-GIT-GOVERNANCE.md`
- `context/decisions/AGENT-BOOTSTRAP-ROUTING.md`
- `context/decisions/HANDOFF-USES-CURATED-DECISION-LIST.md`
- `context/decisions/CONTEXT-GOVERNANCE-CLARIFICATIONS.md`
- `context/decisions/NAMING-AND-OPEN-ISSUE-CLOSURE-CLARIFICATIONS.md`
- `context/decisions/CONTEXT-FREEZE-AND-PROMOTION.md`
- `context/decisions/FOUNDATION-README-SCOPE-AND-ALIGNMENT-CLARIFICATIONS.md`
- `context/decisions/FOUNDATION-README-FREEZE-AND-PROMOTION.md`
- `context/decisions/FOUNDATION-WORKFLOW-AND-GLOBAL-FREEZE-RULE.md`
- `context/decisions/PHASE-MODEL-DECISION-INDEX-AND-LOCAL-HANDOFF-TRANSITION.md`

These are the decisions the next agent must read to reconstruct current truth for this handoff.
The list includes both the current-session decisions and the older decisions this session depends on.

## Newly created decisions in this session

- `context/decisions/FOUNDATION-WORKFLOW-AND-GLOBAL-FREEZE-RULE.md`
- `context/decisions/PHASE-MODEL-DECISION-INDEX-AND-LOCAL-HANDOFF-TRANSITION.md`

## Older decisions this handoff depends on

- `context/decisions/FOUNDATION-SCOPE-AND-OLD-WORK-BOUNDARY.md`
- `context/decisions/FOUNDATION-WORKPLAN-AND-APPROVAL-GATE.md`
- `context/decisions/MANUAL-CONTEXT-STRUCTURE-AND-TRACKERS.md`
- `context/decisions/NAMING-AND-GIT-GOVERNANCE.md`
- `context/decisions/AGENT-BOOTSTRAP-ROUTING.md`
- `context/decisions/HANDOFF-USES-CURATED-DECISION-LIST.md`
- `context/decisions/CONTEXT-GOVERNANCE-CLARIFICATIONS.md`
- `context/decisions/NAMING-AND-OPEN-ISSUE-CLOSURE-CLARIFICATIONS.md`
- `context/decisions/CONTEXT-FREEZE-AND-PROMOTION.md`
- `context/decisions/FOUNDATION-README-SCOPE-AND-ALIGNMENT-CLARIFICATIONS.md`
- `context/decisions/FOUNDATION-README-FREEZE-AND-PROMOTION.md`
- `context/decisions/FOUNDATION-WORKFLOW-AND-GLOBAL-FREEZE-RULE.md`

## Next step

Continue Foundation Step 1 through `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md`.
The next concrete work is to continue review of that artifact against the remaining findings after the decision-routing and local-handoff pushback was fixed.
If the full artifact is later approved for freeze-readiness, move it into freeze approval under the global CEO+CTO freeze rule before returning to the remaining unfrozen foundation support docs.
If the foundation gate later decides foundation is incomplete, the deferred candidates now tracked in `context/OPEN-ISSUES.md` include the known context gap, memory infrastructure, and later script-governance implementation.
