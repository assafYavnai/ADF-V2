# PHASE-MODEL-STEPS-NAMESPACE-AND-LEGACY-MIGRATION

## CONTEXT

Review of the former-step model raised a namespace problem.
The prior target model placed official step folders directly under the phase root and preserved former-step folders as bare slug folders at that same root.

That meant phase-root governed files and folders, such as `CONTRACT.md`, `WORKPLAN.md`, `OPEN-ISSUES.md`, and `artifacts/`, shared a namespace with step slugs.
Even when step slugs are unique as steps, a bare former-step slug could still collide with phase-root governed names.

The discussion clarified that the cleaner fix is not a `former-step-<slug>/` prefix.
Instead, all step folders should be boxed under a phase-local `steps/` namespace.
That preserves the existing rule that a former step loses its execution number and keeps only its slug, while isolating that slug from phase-root names.

## OPTIONS

- Keep step folders directly under the phase root and add a reserved-name blacklist.
- Rename preserved former-step folders with a prefix such as `former-step-<slug>/`.
- Put all step folders under `steps/`, with active steps as `steps/stepNN-<slug>/` and preserved former steps as `steps/<slug>/`.

## DECISION

The agreed target phase-model rules are:

- all step folders live under the phase-local `steps/` namespace
- official instantiated step folders use `steps/stepNN-<slug>/`
- preserved former-step folders use `steps/<slug>/`
- step slugs must be unique within a phase
- the `steps/` namespace isolates step slugs from phase-root governed files and folders
- routing recognizes active steps only when `Current step` points to an instantiated numbered step folder under `steps/`
- preserved former-step folders under `steps/<slug>/` are not active steps until re-instantiated
- re-instantiation renames `steps/<slug>/` to `steps/stepNN-<slug>/`
- the same re-instantiation checkpoint must update the related phase `OPEN-ISSUES.md` entry so the former-step record is removed or closed
- if an instantiated step loses execution order, it is renamed from `steps/stepNN-<slug>/` to `steps/<slug>/`
- the same checkpoint must create or update a phase `OPEN-ISSUES.md` entry pointing to `steps/<slug>/`

At phase-model promotion, legacy phase structures must be migrated into the `steps/` namespace:
- root-level `stepNN-<slug>/` folders become `steps/stepNN-<slug>/`
- root-level preserved former-step `<slug>/` folders become `steps/<slug>/`
- all affected workplan, routing, open-issues, handoff, artifact, and decision references must be updated in the same logical checkpoint

This decision supersedes older wording in `PHASE-MODEL-VIRTUAL-STEPS-AND-FORMER-STEP-FOLDERS` only where that wording placed step folders or preserved former-step folders directly under the phase root.

## APPROVAL

EXPLICIT
