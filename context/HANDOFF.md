# HANDOFF

Status: ACTIVE

## Current state

ADF-V2 is a new clean repository.
The foundation layer is still being defined.
`foundation/README.md` and `CONTEXT.md` both exist as drafts and are not yet frozen by the CEO.

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

These are the decisions the next agent must read to reconstruct current truth for this handoff.
The list includes both the current-session decision and the older decisions this session depends on.

## Newly created decisions in this session

- `context/decisions/CONTEXT-GOVERNANCE-CLARIFICATIONS.md`

## Older decisions this handoff depends on

- `context/decisions/FOUNDATION-SCOPE-AND-OLD-WORK-BOUNDARY.md`
- `context/decisions/FOUNDATION-WORKPLAN-AND-APPROVAL-GATE.md`
- `context/decisions/MANUAL-CONTEXT-STRUCTURE-AND-TRACKERS.md`
- `context/decisions/NAMING-AND-GIT-GOVERNANCE.md`
- `context/decisions/AGENT-BOOTSTRAP-ROUTING.md`
- `context/decisions/HANDOFF-USES-CURATED-DECISION-LIST.md`

## Next step

Continue Foundation Step 1.
The next concrete work is to run CEO freeze review on `CONTEXT.md` and then continue the remaining Foundation Step 1 freeze review on the other draft foundation docs.
