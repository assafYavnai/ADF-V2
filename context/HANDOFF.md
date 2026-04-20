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
Reviewer pushback on the promoted-phase root model and transition from the current bootstrap tree was then addressed in the draft.
The draft now makes root promoted phases selectable rather than implicitly active, makes phase number a reviewed recommendation-order number among open promoted phases, separates phase close from next-phase selection, and records the intended normalization of `phase0-foundation` and `phase1-Strategic_Definition` at the later phase-model promotion checkpoint.
That promoted-root, ordering, and transition rule was then also saved as an explicit decision.
Reviewer pushback on active-step tracking and close-gate step flow was then addressed in the draft.
The draft now makes `Current step` an explicit `WORKPLAN.md` field, keeps default next-step flow in the ordered implementation step list, and keeps post-implementation close-gate follow-up work inside the workplan rather than in a separate tracker.
That workplan-authority and close-gate-flow rule was then saved as another explicit decision.
Reviewer pushback on approval ordering, promotion ownership, and movement to `phases/complete/` was then addressed in the draft.
The draft now defines a two-gate flow of freeze-ready, freeze approval, review-fix cycle, close-ready, close approval, promotion, and post-promotion state, while making promotion a mechanical phase-owned step rather than another approval gate.
That two-gate, promotion, and routing-update rule was then saved as another explicit decision.
Reviewer pushback on artifact governance and promotion enforceability was then addressed in the draft.
The draft now uses the simpler boxed artifact model of step `drafts/`, phase `artifacts/`, and phase-owned promotion to canonical repo locations, while removing the earlier need for separate per-artifact metadata at this stage.
That step-drafts, phase-artifacts, and contract-owned promotion rule was then saved as another explicit decision.
Second-pass reviewer pushback on freeze-ready versus close-ready sequencing was then addressed in the draft.
The draft now makes freeze recommendation happen at the freeze-ready checkpoint before review, and moves close-gate follow-up work to after the review-fix cycle.
That lifecycle-sequencing clarification was then saved as another explicit decision so later agents do not have to reconcile conflicting wording by inference.
Second-pass reviewer pushback on the decisions-folder contract was then addressed in the draft.
The draft now makes `context/decisions/INDEX.md` an explicitly governed support file in the target model, while keeping the current bootstrap `frozen decisions only` folder contract authoritative until the later phase-model promotion checkpoint.
That decisions-folder supersession rule was then saved as another explicit decision so later agents do not have to invent an exception by inference.
The open-issues audit-trail question was then clarified in the draft.
The draft now keeps `OPEN-ISSUES.md` as a current-state surface and uses git checkpoints, not a new local activity file, as the governed audit trail for open-issue lifecycle changes.
That git-backed open-issues audit-trail rule was then saved as another explicit decision.
Second-pass reviewer pushback on promoted-phase inventory was then addressed in the draft.
The draft now makes promotion eligibility depend on ready phase `CONTRACT.md` and `WORKPLAN.md`, while requiring the promotion checkpoint itself to end with a full promoted phase box, including phase `OPEN-ISSUES.md` and the first step box.
That full-phase-box promotion rule was then saved as another explicit decision so later agents and scripts do not invent partial promotion behavior.
Second-pass reviewer pushback on step numbering and step-folder identity was then addressed in the draft.
The draft now makes the workplan step list virtual until instantiation, makes numbered step folders mean official execution order in practice, and makes reordered instantiated steps lose their number and fall back to slug-only former-step folders tracked in phase `OPEN-ISSUES.md` until re-instantiation or explicit disposition.
That virtual-step, re-instantiation, and former-step tracking rule was then saved as another explicit decision.

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
- `context/decisions/PHASE-MODEL-PROMOTED-ROOT-ORDER-AND-TRANSITION.md`
- `context/decisions/PHASE-MODEL-WORKPLAN-CURRENT-STEP-AND-CLOSE-GATE-FLOW.md`
- `context/decisions/PHASE-MODEL-TWO-GATE-APPROVAL-AND-PROMOTION-FLOW.md`
- `context/decisions/PHASE-MODEL-STEP-DRAFTS-AND-PHASE-ARTIFACTS.md`
- `context/decisions/PHASE-MODEL-FREEZE-READY-PRECEDES-CLOSE-READY.md`
- `context/decisions/PHASE-MODEL-DECISIONS-FOLDER-CONTRACT-SUPERSESSION.md`
- `context/decisions/PHASE-MODEL-OPEN-ISSUES-USE-GIT-FOR-AUDIT-TRAIL.md`
- `context/decisions/PHASE-MODEL-PROMOTION-MUST-MATERIALIZE-FULL-PHASE-BOX.md`
- `context/decisions/PHASE-MODEL-VIRTUAL-STEPS-AND-FORMER-STEP-FOLDERS.md`

These are the decisions the next agent must read to reconstruct current truth for this handoff.
The list includes both the current-session decisions and the older decisions this session depends on.

## Newly created decisions in this session

- `context/decisions/FOUNDATION-WORKFLOW-AND-GLOBAL-FREEZE-RULE.md`
- `context/decisions/PHASE-MODEL-DECISION-INDEX-AND-LOCAL-HANDOFF-TRANSITION.md`
- `context/decisions/PHASE-MODEL-PROMOTED-ROOT-ORDER-AND-TRANSITION.md`
- `context/decisions/PHASE-MODEL-WORKPLAN-CURRENT-STEP-AND-CLOSE-GATE-FLOW.md`
- `context/decisions/PHASE-MODEL-TWO-GATE-APPROVAL-AND-PROMOTION-FLOW.md`
- `context/decisions/PHASE-MODEL-STEP-DRAFTS-AND-PHASE-ARTIFACTS.md`
- `context/decisions/PHASE-MODEL-FREEZE-READY-PRECEDES-CLOSE-READY.md`
- `context/decisions/PHASE-MODEL-DECISIONS-FOLDER-CONTRACT-SUPERSESSION.md`
- `context/decisions/PHASE-MODEL-OPEN-ISSUES-USE-GIT-FOR-AUDIT-TRAIL.md`
- `context/decisions/PHASE-MODEL-PROMOTION-MUST-MATERIALIZE-FULL-PHASE-BOX.md`
- `context/decisions/PHASE-MODEL-VIRTUAL-STEPS-AND-FORMER-STEP-FOLDERS.md`

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
The promoted-root, renumbering, and close-versus-selection pushback is also now fixed in the draft.
The workplan current-step and close-gate-flow pushback is also now fixed in the draft.
The two-gate approval, promotion, and routing-update pushback is also now fixed in the draft.
The artifact-governance and promotion-enforceability pushback is also now fixed in the draft.
The freeze-ready versus close-ready sequencing contradiction is also now fixed in the draft.
The decisions-folder contract contradiction is also now fixed in the draft.
The open-issues audit-trail rule is also now fixed in the draft.
The promoted-phase inventory contradiction is also now fixed in the draft.
The step numbering and former-step tracking contradiction is also now fixed in the draft.
If the full artifact is later approved for freeze-readiness, move it into freeze approval under the global CEO+CTO freeze rule before returning to the remaining unfrozen foundation support docs.
If the foundation gate later decides foundation is incomplete, the deferred candidates now tracked in `context/OPEN-ISSUES.md` include the known context gap, memory infrastructure, and later script-governance implementation.
