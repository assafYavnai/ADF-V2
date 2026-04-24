# PHASE-MODEL-PROMOTION-MUST-MATERIALIZE-FULL-PHASE-BOX

## CONTEXT

The second review pass on `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` found that the draft still gave two different signals about promoted-phase creation.
One section said promotion from backlog into the promoted root required only `CONTRACT.md` and `WORKPLAN.md`.
Another section said a promoted phase folder must contain `CONTRACT.md`, `WORKPLAN.md`, `OPEN-ISSUES.md`, and one or more step folders.
That left an unresolved question about whether `OPEN-ISSUES.md` and the first step box had to exist before promotion or could be created during promotion.
A later activation-boundary clarification applied the same rule to `phases/phase0-foundation/` during phase-model promotion.
The target model may not activate with foundation structural compliance deferred to a later step.

## OPTIONS

- Require all promoted-phase inventory to already exist before promotion can begin.
- Let promotion create missing inventory later in follow-up cleanup after the phase is already at the promoted root.
- Allow promotion eligibility to be based on ready `CONTRACT.md` and `WORKPLAN.md`, but require the promotion checkpoint itself to end with the full promoted-phase box materialized.

## DECISION

The agreed target phase-model rules are:

- promotion eligibility is based on ready and compliant phase `CONTRACT.md` and `WORKPLAN.md`
- promotion execution must materialize the full minimum promoted-phase box in the same logical checkpoint
- by the end of that checkpoint, the promoted phase must contain:
  - `CONTRACT.md`
  - `WORKPLAN.md`
  - `OPEN-ISSUES.md`
  - `steps/`
  - at least one `steps/stepNN-<slug>/` folder
- that first step box must contain:
  - `CONTRACT.md`
  - `OPEN-ISSUES.md`
- the phase `CONTRACT.md`, phase `WORKPLAN.md`, and first step `CONTRACT.md` must already be compatible with each other at promotion time
- the missing `OPEN-ISSUES.md` files and first step box may either already exist inside the backlog candidate or be created atomically during the promotion checkpoint
- no phase may appear in the promoted root as a partially initialized box at the end of a checkpoint
- the phase-model promotion checkpoint must end with `phases/phase0-foundation/` materialized as a full compliant promoted phase box before the target model becomes active
- Foundation Step 2 may not be used to complete missing target structural inventory after activation

This decision closes the promoted-phase creation ambiguity while preserving the boxed model and leaving scripts no room to invent partial promotion behavior.

## APPROVAL

EXPLICIT
