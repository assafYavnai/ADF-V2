# PHASE-MODEL-DECISION-INDEX-AND-LOCAL-HANDOFF-TRANSITION

## CONTEXT

The review of `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` raised a critical pushback on decision routing.
The draft routed agents through `context/decisions/INDEX.md`, but current frozen foundation-bootstrap truth still uses global `context/HANDOFF.md` as the curated decision-read surface.
The review also exposed that the local `HANDOFF.md` model had been discussed but not yet written down as governed repo truth, which risked repeating the same confusion later.

## PUSHBACK

The core pushback was:
- the draft would split decision authority unless it explicitly states how current global handoff governance is superseded
- the draft still risked adding maintenance-heavy shadow tracking if status or current-step logic was mirrored outside `WORKPLAN.md`
- the local `HANDOFF.md` idea remained incomplete until its creation, update, and usage rules were written down explicitly

The related CEO guidance in the discussion was:
- do not invent more mechanisms to track state
- current step should live in `WORKPLAN.md`
- reason for unfreezing or revising the workplan should be captured as a decision
- `context/STATUS.md` should be treated as obsolete in the target model rather than carried forward as a second state surface
- any `HANDOFF.md` kept in the target model should be local to the boxed scope, optional by nature, and read only if routing tells the agent to check for it

## DISCUSSION SUMMARY

The discussion re-tested the problem from first principles instead of starting from the current bootstrap files.
That led to three clarifications.

First, status and sequencing belong to the work container that owns execution.
For a phase, that owner is `WORKPLAN.md`.
So the target model should not introduce a separate phase-local `STATUS.md`, and routing should not become a second owner of step sequencing.

Second, the only thing a handoff file can justify owning is continuity that is hard to reconstruct from boxed truth.
That means `HANDOFF.md` is not a scope file, not a sequencing file, not a gate file, and not a curated decision-membership file.
It is only an optional continuity snapshot for the relevant local scope.

Third, the reviewer pushback was valid unless the transition from current global handoff governance to target phase-model governance was made explicit.
The draft therefore needed a same-checkpoint migration rule so the model would not become active piecemeal.

## OPTIONS

- Keep global `context/HANDOFF.md` as the long-term curated decision-read surface and let the phase model point to it.
- Move decision curation to `context/decisions/INDEX.md` in the target phase model, while keeping global `context/HANDOFF.md` only as a temporary foundation-bootstrap surface until promotion.
- Keep or introduce separate status-style trackers for current and next step outside `WORKPLAN.md`.
- Keep `HANDOFF.md` global.
- Make `HANDOFF.md` local and optional in the target phase model, with explicit usage rules.

## DECISION

The agreed target phase-model rules are:

- `WORKPLAN.md` is the authority for current and next step inside a phase.
- phase routing must not manage step sequencing
- a separate phase-local `STATUS.md` is not introduced in the target model
- if the frozen workplan flow changes, `WORKPLAN.md` must be unfrozen and revised
- the reason for that revision must be captured in the revision decision and in the revised `WORKPLAN.md`

- `context/decisions/INDEX.md` is the curated decision-read surface in the target phase model
- global `context/HANDOFF.md` must not remain the curated decision-membership surface once the phase model is promoted
- until the phase model is frozen and promoted, the current foundation-bootstrap runtime may still use the existing global `context/HANDOFF.md` decision-read list
- when the phase model is promoted, the same logical checkpoint must:
  - create or update `context/decisions/INDEX.md`
  - update `phases/ROUTING.md` to point to it
  - remove any requirement that global `context/HANDOFF.md` curate decision membership
  - keep the checkpoint self-consistent and commit it as one logical repo-truth change

- `HANDOFF.md` is optional and local in the target phase model
- allowed locations are:
  - `phases/phaseNNN-<slug>/HANDOFF.md`
  - `phases/phaseNNN-<slug>/stepNN-<slug>/HANDOFF.md`
- local `HANDOFF.md` is continuity-only
- local `HANDOFF.md` may be created only:
  - when an actual handoff is needed
  - when the CEO explicitly asks to preserve cross-session continuity for that local scope
- local `HANDOFF.md` may be updated only when a meaningful local-state change would be hard to reconstruct from boxed files alone
- local `HANDOFF.md` must not become a routine progress mirror
- local `HANDOFF.md` must not own:
  - scope authority
  - current-step or next-step authority
  - decision membership authority
  - gate authority
  - approval state not already reflected in boxed files
- `phases/ROUTING.md` must instruct agents to:
  - read the mandatory boxed files first
  - read `context/decisions/INDEX.md`
  - read only the listed decision files
  - then check for local `HANDOFF.md` in the active scope if it exists
  - prefer step-local handoff over phase-local handoff when both could apply

This decision is about the target phase-model contract and its transition rule.
It does not by itself rewrite the currently active foundation-bootstrap runtime until the phase-model promotion checkpoint is executed.

## APPROVAL

EXPLICIT
