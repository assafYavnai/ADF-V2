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
The root bootstrap files now exist and remain the current transition runtime.
The boxed `AGENTS.md` model is documented only inside the phase-model draft as a promotion-time template, not applied to the live bootstrap files during this transition.
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
The draft now makes `Current step` an explicit `WORKPLAN.md` field, keeps default next-step flow in the ordered implementation step list, and keeps post-implementation freeze-ready preparation and close-gate follow-up work inside the workplan rather than in a separate tracker.
That workplan-authority and close-gate-flow rule was then saved as another explicit decision.
Reviewer pushback on approval ordering, promotion ownership, and movement to `phases/complete/` was then addressed in the draft.
The draft now defines a two-gate flow of freeze-ready, freeze approval, review-fix cycle, close-ready, close approval, promotion, and post-promotion state, while making promotion a mechanical phase-owned step rather than another approval gate.
That two-gate, promotion, and routing-update rule was then saved as another explicit decision.
Reviewer pushback on artifact governance and promotion enforceability was then addressed in the draft.
The draft now uses the simpler boxed artifact model of `steps/<step>/drafts/`, phase `artifacts/`, and phase-owned promotion to canonical repo locations, while removing the earlier need for separate per-artifact metadata at this stage.
That step-drafts, phase-artifacts, and contract-owned promotion rule was then saved as another explicit decision.
Second-pass reviewer pushback on freeze-ready versus close-ready sequencing was then addressed in the draft.
The draft now makes freeze recommendation happen at the freeze-ready checkpoint before review, and moves close-gate follow-up work to after the review-fix cycle.
That lifecycle-sequencing clarification was then saved as another explicit decision so later agents do not have to reconcile conflicting wording by inference.
Second-pass reviewer pushback on the decisions-folder contract was then addressed in the draft.
The draft now makes `context/decisions/INDEX.md` an explicitly governed support file in the target model, while keeping the current bootstrap `frozen decisions only` folder contract authoritative until the later phase-model promotion checkpoint.
That decisions-folder supersession rule was then saved as another explicit decision so later agents do not have to invent an exception by inference.
The open-issues audit-trail question was then clarified in the draft.
The draft now keeps `OPEN-ISSUES.md` as a current-state surface and uses git checkpoints, not a new local activity file, as the governed audit trail for open-issue lifecycle changes.
The draft now also defines the lean file-friendly open issue entry contract, including title-as-handle, evidence, impact, next action, closure condition, owner, last updated, and source session.
That git-backed open-issues audit-trail and entry-contract rule was then saved as another explicit decision.
Second-pass reviewer pushback on promoted-phase inventory was then addressed in the draft.
The draft now makes promotion eligibility depend on ready phase `CONTRACT.md` and `WORKPLAN.md`, while requiring the promotion checkpoint itself to end with a full promoted phase box, including phase `OPEN-ISSUES.md` and the first step box.
That full-phase-box promotion rule was then saved as another explicit decision so later agents and scripts do not invent partial promotion behavior.
Second-pass reviewer pushback on step numbering and step-folder identity was then addressed in the draft.
The draft now makes the workplan step list virtual until instantiation, boxes all step folders under `steps/`, makes numbered step folders mean official execution order in practice, and makes reordered instantiated steps lose their number and fall back to slug-only former-step folders under `steps/` tracked in phase `OPEN-ISSUES.md` until re-instantiation or explicit disposition.
That virtual-step, re-instantiation, and former-step tracking rule was then saved as another explicit decision.
The backlog-shape and no-exceptions rule was then clarified in the draft.
The draft now removes target-model structural exceptions, makes backlog candidates folder-based rather than `README.md`-based, and requires legacy nested backlog structures to be normalized before target-model activation.
That no-exceptions and folder-based backlog rule was then saved as another explicit decision.
The live `system-definition` backlog candidate was then normalized to match that model.
Its backlog `WORKPLAN.md` was kept, its nested legacy `phases/` subtree was removed, and that concrete normalization path was saved as another explicit decision so later agents do not recreate the old shape.
The stale local artifacts-readme freeze wording was then corrected to match frozen `CONTEXT.md`.
The local readme now points to the global freeze rule instead of implying CEO-only artifact approval, and that correction was saved as another explicit decision.
The target-model treatment of global `context/STATUS.md` was then made explicit in the draft.
The draft now says global `context/STATUS.md` is bootstrap-only and is retired at phase-model promotion, with target operational state reconstructed from routing, workplan, and open-issues surfaces.
That global-status retirement rule was then saved as another explicit decision.
A deeper carry-through audit then found one remaining partial-application gap in routing wording.
The draft routing section now explicitly recognizes only instantiated numbered step folders under `steps/` as active steps, and that alignment was saved as another explicit decision instead of silently rewriting older frozen decisions.
That same deeper audit then found one stale bootstrap freeze sentence in frozen `CONTEXT.md`.
The bootstrap artifact-freeze wording was then normalized so the request and rejection path both use the already agreed global CEO+CTO freeze rule instead of drifting back to CEO-only phrasing.
The remaining structural review issue on approval-state determinism was then addressed in the draft.
The draft now explicitly separates document approval state from scope lifecycle state, makes phase `WORKPLAN.md` the canonical runtime-state owner for both phase and instantiated-step lifecycle, defines the required workplan runtime-state schema, keeps contracts scoped to definition plus their own document approval state, keeps `OPEN-ISSUES.md` blocker-only, and makes git checkpoints the audit trail instead of introducing a new tracker layer.
Deferred foundation-phase concerns that must survive current-step promotion were then moved out of the bootstrap global open-issues pool and into `phases/phase0-foundation/OPEN-ISSUES.md`.
That phase-local file now carries the known context gap, persistent memory support, traceability gaps, KPI support, and later script governance as deferred foundation work.
The global-vs-phase open-issues boundary was then clarified so `context/OPEN-ISSUES.md` remains global/bootstrap while foundation-scoped deferred items live in `phases/phase0-foundation/OPEN-ISSUES.md`, with promotion-time triage required.
Reviewer pushback about bootstrap entrypoint migration was then corrected by clarifying the target top-level boxed traversal model.
The boxed `AGENTS.md` shape is kept as a promotion-time template inside the phase-model draft.
The live bootstrap files must not be changed until the phase model is promoted and implemented.
Decision carry-through was then made explicit as both a global rule in `RULES.md` and a local phase-model requirement.
Approved decisions cannot be described as integrated, fixed, closed, or implemented until all dependent surfaces are updated or explicitly marked unchanged with reason.
The current seven-finding review cycle then began.
Finding 1, the missing review-fix current-work schema, was addressed by making phase `WORKPLAN.md` own `## Review-Fix Cycle`, adding `review-fix` as a `Current step type`, and defining local substeps as non-governed descriptive planning inside a step.

## Session pointers

- `phases/phase0-foundation/WORKPLAN.md`
- `phases/phase0-foundation/OPEN-ISSUES.md`
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
- `context/decisions/PHASE-MODEL-NO-EXCEPTIONS-AND-FOLDER-BASED-BACKLOG.md`
- `context/decisions/SYSTEM-DEFINITION-BACKLOG-NORMALIZATION.md`
- `context/decisions/ARTIFACTS-README-USES-GLOBAL-FREEZE-RULE.md`
- `context/decisions/PHASE-MODEL-RETIRE-GLOBAL-STATUS-AFTER-PROMOTION.md`
- `context/decisions/PHASE-MODEL-ROUTING-USES-INSTANTIATED-NUMBERED-STEPS.md`
- `context/decisions/CONTEXT-ARTIFACT-FREEZE-WORDING-USES-GLOBAL-RULE.md`
- `context/decisions/PHASE-MODEL-SEPARATES-DOCUMENT-APPROVAL-FROM-RUNTIME-STATE.md`
- `context/decisions/AGENT-ENTRY-USES-BOXED-LAYER-TRAVERSAL.md`
- `context/decisions/DECISION-CARRY-THROUGH-IS-MANDATORY.md`
- `context/decisions/PHASE-MODEL-OPEN-ISSUES-TRANSITION-TRIAGE.md`
- `context/decisions/PHASE-MODEL-STEPS-NAMESPACE-AND-LEGACY-MIGRATION.md`
- `context/decisions/PHASE-MODEL-REVIEW-FIX-CYCLE-AND-SUBSTEPS.md`

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
- `context/decisions/PHASE-MODEL-NO-EXCEPTIONS-AND-FOLDER-BASED-BACKLOG.md`
- `context/decisions/SYSTEM-DEFINITION-BACKLOG-NORMALIZATION.md`
- `context/decisions/ARTIFACTS-README-USES-GLOBAL-FREEZE-RULE.md`
- `context/decisions/PHASE-MODEL-RETIRE-GLOBAL-STATUS-AFTER-PROMOTION.md`
- `context/decisions/PHASE-MODEL-ROUTING-USES-INSTANTIATED-NUMBERED-STEPS.md`
- `context/decisions/CONTEXT-ARTIFACT-FREEZE-WORDING-USES-GLOBAL-RULE.md`
- `context/decisions/PHASE-MODEL-SEPARATES-DOCUMENT-APPROVAL-FROM-RUNTIME-STATE.md`
- `context/decisions/AGENT-ENTRY-USES-BOXED-LAYER-TRAVERSAL.md`
- `context/decisions/DECISION-CARRY-THROUGH-IS-MANDATORY.md`
- `context/decisions/PHASE-MODEL-OPEN-ISSUES-TRANSITION-TRIAGE.md`
- `context/decisions/PHASE-MODEL-STEPS-NAMESPACE-AND-LEGACY-MIGRATION.md`
- `context/decisions/PHASE-MODEL-REVIEW-FIX-CYCLE-AND-SUBSTEPS.md`

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
The known six-finding review set has now been addressed in the phase-model draft and carried through dependent decision/status surfaces.
The next concrete work is to run a final audit or review pass before asking for freeze-readiness approval.
The promoted-root, renumbering, and close-versus-selection pushback is also now fixed in the draft.
The workplan current-step and close-gate-flow pushback is also now fixed in the draft.
The two-gate approval, promotion, and routing-update pushback is also now fixed in the draft.
The artifact-governance and promotion-enforceability pushback is also now fixed in the draft.
The freeze-ready versus close-ready sequencing contradiction is also now fixed in the draft.
The decisions-folder contract contradiction is also now fixed in the draft.
The open-issues audit-trail and item-schema finding is also now fixed in the draft.
The promoted-phase inventory contradiction is also now fixed in the draft.
The step numbering and former-step tracking contradiction is also now fixed in the draft.
The backlog-shape and no-exceptions contradiction is also now fixed in the draft.
The live `system-definition` backlog candidate is also now normalized to the folder-based backlog model.
The local artifacts-readme freeze wording is also now aligned with frozen `CONTEXT.md`.
The global `context/STATUS.md` retirement rule is also now explicitly carried through the target-model transition.
The routing step-selection wording is also now fully aligned with the virtual-step and former-step model.
The bootstrap artifact-freeze wording in frozen `CONTEXT.md` is also now internally aligned with the same global freeze rule.
The approval-state determinism gap is also now fixed by separating document approval from runtime lifecycle state, making the phase workplan the canonical runtime-state owner, and defining the required workplan runtime-state schema.
Deferred foundation-phase concerns that must survive current-step promotion are also now tracked in `phases/phase0-foundation/OPEN-ISSUES.md` instead of only in the bootstrap global open-issues file.
The global-vs-phase open-issues transition boundary and required promotion-time triage are also now saved as an explicit decision.
The bootstrap entrypoint migration finding is addressed in the phase-model draft by defining the promotion-time boxed `AGENTS.md` template and keeping live bootstrap implementation deferred until promotion.
The decision carry-through rule is also now recorded globally in `RULES.md`, locally in the phase-model draft, and as an explicit decision.
The former-step collision finding is now addressed by boxing all step folders under the phase-local `steps/` namespace and adding a promotion-time migration task for legacy root-level step folders.
The current seven-finding review cycle is now being handled one finding at a time.
Finding 1 is addressed by the new governed review-fix cycle schema in `WORKPLAN.md` and the explicit rule that substeps remain local, non-governed step planning.
The next review item to discuss is finding 2, the freeze / promotion approval authority finding.
If the full artifact is later approved for freeze-readiness, move it into freeze approval under the global CEO+CTO freeze rule before returning to the remaining unfrozen foundation support docs.
If the foundation gate later decides foundation is incomplete, the deferred foundation-phase concerns now tracked in `phases/phase0-foundation/OPEN-ISSUES.md` include the known context gap, persistent memory, traceability gaps, KPI support, and later script-governance implementation.
