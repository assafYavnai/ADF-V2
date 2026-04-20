# PHASE-MODEL-PROMOTION-MUST-MATERIALIZE-FULL-PHASE-BOX

## CONTEXT

The second review pass on `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` found that the draft still gave two different signals about promoted-phase creation.
One section said promotion from backlog into the promoted root required only `CONTRACT.md` and `WORKPLAN.md`.
Another section said a promoted phase folder must contain `CONTRACT.md`, `WORKPLAN.md`, `OPEN-ISSUES.md`, and one or more step folders.
That left an unresolved question about whether `OPEN-ISSUES.md` and the first step box had to exist before promotion or could be created during promotion.

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
  - at least one `stepNN-<slug>/` folder
- that first step box must contain:
  - `CONTRACT.md`
  - `OPEN-ISSUES.md`
- the phase `CONTRACT.md`, phase `WORKPLAN.md`, and first step `CONTRACT.md` must already be compatible with each other at promotion time
- the missing `OPEN-ISSUES.md` files and first step box may either already exist inside the backlog candidate or be created atomically during the promotion checkpoint
- no phase may appear in the promoted root as a partially initialized box at the end of a checkpoint

This decision closes the promoted-phase creation ambiguity while preserving the boxed model and leaving scripts no room to invent partial promotion behavior.

## APPROVAL

EXPLICIT
