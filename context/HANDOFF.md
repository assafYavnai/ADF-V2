# HANDOFF

Status: ACTIVE

## Current state

ADF-V2 is a new clean repository.
The foundation layer is still being defined.
`CONTEXT.md` is now frozen.
`foundation/README.md` is now frozen.

## Current task

Complete Foundation Step 1 by defining and aligning the foundation framework files.

## Current step

Foundation Step 1

## Session summary

This repository is still building the foundation framework itself.
The current discussion is defining how context works, how files should be shaped, and how agents should preserve continuity without hidden assumptions.
The root bootstrap files now exist, and `AGENTS.md` routes agents through the foundation workplan, foundation readme, context files, and rules before substantive work.
The explicit decisions from this discussion are now saved under `context/decisions/`.
For handoff, the next agent must read the curated decision list below rather than trying to infer truth from the full decisions folder.
The `CONTEXT.md` contract gaps found during review were addressed in this session so the draft now matches actual repo practice more closely.
The naming-rule scope and open-issue closure rule were tightened again in this session to remove the last remaining governance ambiguities.
`CONTEXT.md` was then explicitly approved, frozen, and promoted in place.
`foundation/README.md` was then rewritten to match the live foundation contract and the mandatory future-alignment requirement around CEO / CTO / DEV.
`foundation/README.md` was then explicitly approved, frozen, and promoted in place.
The foundation work model was then clarified so the gate is a post-freeze check, not a step, and freeze was made explicit as a global CEO+CTO approval rule.
Additional deferred foundation concerns were then captured in `OPEN-ISSUES.md` so they stay visible without widening the current active step.

## Session pointers

- `foundation/WORKPLAN.md`
- `foundation/README.md`
- `CONTEXT.md`
- `RULES.md`
- `AGENTS.md`
- `CLAUDE.md`
- `GEMINI.md`
- `context/STATUS.md`
- `context/OPEN-ISSUES.md`

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

These are the decisions the next agent must read to reconstruct current truth for this handoff.
The list includes both the current-session decision and the older decisions this session depends on.

## Newly created decisions in this session

- `context/decisions/FOUNDATION-WORKFLOW-AND-GLOBAL-FREEZE-RULE.md`

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

## Next step

Continue Foundation Step 1.
The next concrete work is to run CEO freeze review on the remaining unfrozen foundation support docs, freeze them under the global CEO+CTO freeze rule, and then run the foundation gate as a post-freeze check.
If the gate later decides foundation is incomplete, the deferred candidates now tracked in `context/OPEN-ISSUES.md` include phase folder structure, context-gap implementation, and memory infrastructure.
