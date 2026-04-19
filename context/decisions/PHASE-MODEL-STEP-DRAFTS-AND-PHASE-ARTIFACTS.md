# PHASE-MODEL-STEP-DRAFTS-AND-PHASE-ARTIFACTS

## CONTEXT

The review of `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` raised a pushback that the artifact and promotion rules were not yet enforceable enough.
The earlier draft allowed both step and phase draft-artifact behavior, referred to artifact metadata without defining its schema, and still left too much room for scripts or agents to invent how artifact movement should work.

## PUSHBACK

The core pushback was:
- the artifact model still carried unnecessary ambiguity about where artifacts are authored
- the draft still implied phase-local draft creation even though the phase is meant to collect outputs rather than author them
- the draft referred to artifact metadata without defining it
- promotion rules were not yet simple enough to follow without inference

## DISCUSSION SUMMARY

The discussion simplified the model from first principles.
The key insight was that artifacts can be authored only inside steps.
The phase does not create draft artifacts of its own.
Instead, the phase collects approved step outputs and is the only scope that may later promote those collected artifacts toward canonical repo truth.

This creates a stronger boxed model:
- steps author drafts
- the phase collects approved outputs
- canonical repo truth is reached only through phase promotion

The discussion therefore replaced the earlier artifact model with:
- `stepNN-<slug>/drafts/`
- `phases/phaseNNN-<slug>/artifacts/`
- canonical repo destinations only after phase close and phase promotion

The discussion also removed the need for a separate per-artifact metadata schema at this stage.
Instead, the contracts become the authoritative source for:
- what outputs exist
- what outputs are promotable
- what conditions must be met before promotion
- where promoted artifacts move next

The discussion also clarified rework.
If a collected phase artifact later needs revision before phase close, it must return to explicit step scope for rework rather than being revised ad hoc inside phase scope.

## OPTIONS

- Keep both step-local and phase-local draft artifact creation.
- Add a separate per-artifact metadata schema to carry movement rules.
- Simplify the model so that steps author drafts, phases collect approved outputs, and contracts define all promotion behavior.

## DECISION

The agreed target phase-model artifact rules are:

- artifacts are authored only inside steps
- the phase does not create draft artifacts of its own
- the phase collects approved step outputs and is the only scope that may promote those collected artifacts toward canonical repo truth

- artifact storage is boxed as:
  - step `drafts/`
  - phase `artifacts/`
  - canonical repo destinations outside the active phase only after phase promotion

- `drafts/` is optional inside a step and is created only when that step needs to author draft outputs
- `artifacts/` is optional at phase scope and is created only when the phase first collects approved step outputs

- the minimum step contract must include a draft-output promotion rule
- the minimum phase contract must include an artifact collection and promotion rule

- the step contract must define:
  - which draft outputs are promotable to phase scope
  - any conditions that must be satisfied before those outputs may be collected by the phase

- the phase contract must define:
  - which collected phase artifacts are promotable to canonical repo locations at phase close
  - the canonical promotion targets for those artifacts

- when a step closes, the phase scope executes step promotion under the step contract promotion rule
- approved step outputs move from `stepNN-<slug>/drafts/` into the phase-root `artifacts/` folder

- while the phase is active, `phases/phaseNNN-<slug>/artifacts/` holds collected phase-owned artifacts in isolation
- when a phase closes, the phase scope executes phase promotion under the phase contract artifact collection and promotion rule
- selected collected artifacts move from the phase-root `artifacts/` folder to the canonical repo locations named by the phase contract

- if a collected artifact later needs revision before phase close, it must return to an explicit step `drafts/` scope for rework
- that rework may happen in the original step or in a new explicit revision step
- it must not be revised ad hoc at phase scope

- an artifact is not ready for freeze review unless:
  - its required content is complete
  - its required verification is complete
  - the relevant step or phase contract defines enough promotion information for the next allowed move

- the artifact model does not require a separate per-artifact metadata schema at this stage
- contracts are the authoritative source for what outputs exist, what may be promoted, and where promoted artifacts may move

This decision closes the artifact-governance ambiguity by simplifying the boxed model rather than adding more tracking surfaces.

## APPROVAL

EXPLICIT
