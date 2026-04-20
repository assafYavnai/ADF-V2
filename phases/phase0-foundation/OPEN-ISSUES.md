# OPEN-ISSUES

Status: ACTIVE

This file holds deferred foundation-phase concerns that must survive Foundation Step 1 review and later step promotion.
These items belong to foundation phase scope, not only to the current active step.

## O-005 - Implement the known context gap

The known context gap still needs an explicit implementation decision.
The gap is that important non-frozen working context can still be lost between sessions if it is neither frozen truth, current operating state, nor a deferred open issue.

Follow-up should define the active working-context / non-frozen context surface described in `phases/backlog/memory/context.md`.
Session closeout should then normalize important knowledge into exactly one governed sink:
- frozen truth
- active working context
- deferred issue
- discarded / no longer needed

This is not the current active step.
Keep it in foundation phase scope unless the foundation gate later defers it out of the phase.

## O-006 - Implement persistent memory support as part of foundation

Persistent memory still needs explicit governed design and implementation.
That support should cover the backlog material under `phases/backlog/memory/`, including:
- active working context that preserves important non-frozen learnings across sessions
- durable user profile / personal-preference memory
- durable user operating-rules memory
- deterministic read and update rules so future agents know how to use that memory without inference

Examples from the current backlog include:
- user personal preferences for how agents should answer or explain
- user operating rules that affect how prompts combining questions and actions should be handled
- expectations such as case-insensitive treatment of user file references when repo conventions use canonical casing

This is not the current active step.
It should be revisited under a later approved foundation step if foundation remains open.

## O-007 - Close the current traceability gaps in governed execution

Current governed audit trail is strong at logical checkpoint granularity but incomplete between checkpoints.
The currently weak or missing trace surfaces are:
- uncommitted work
- minute-by-minute progress
- abandoned or rejected implementation paths unless they are written into a governed file
- detailed test execution evidence unless it is persisted in repo truth
- fine-grained activity hidden inside a large commit

A future foundation step should decide whether checkpoint-level traceability is sufficient or whether a governed intermediate trace surface is needed.
This issue must survive current-step promotion because it belongs to foundation-phase governance, not only to the current review step.

## O-008 - Script-governance implementation remains deferred after the phase model draft

The phase-model draft is now intended to be script-ready, but script governance is not part of the current implementation layer.
If script enforcement is later chosen, it should enforce the frozen model rather than redefine it.

Examples include:
- routing enforcement
- gate enforcement
- promotion and demotion enforcement

This is not the current active step.
It should be revisited after the phase model is frozen if implementation is later approved.

## O-009 - Add KPI support for governed execution

KPI support is still missing from the current foundation model.
A future foundation step should define:
- which KPIs matter at foundation, phase, and step scope
- how KPI current state is captured
- where KPI historical trail lives
- how KPI review interacts with gates, review cycles, and closeout

Examples may include:
- execution cadence
- review finding volume and closure rate
- verification outcomes
- deferred-item flow
- promotion throughput

This is not the current active step.
It should be revisited only if foundation remains open after the current step.
