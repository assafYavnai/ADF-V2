# PHASE-MODEL-ACTIVATION-REQUIRES-COMPLIANT-FOUNDATION-BOX

## CONTEXT

The seven-finding review found that the phase-model transition wording still mixed target activation with later foundation normalization.
The draft said the target model must not activate piecemeal and that no structural exceptions are allowed, but also said foundation normalization into full target-model compliance becomes Foundation Step 2.

## PUSHBACK

The pushback was:
- target activation requires structural compliance
- `phases/phase0-foundation/` cannot become the active target phase while still structurally non-compliant
- Foundation Step 2 wording could be read as permission to activate the target model first and normalize the active phase later
- that reading contradicts the no-exceptions rule

## DISCUSSION SUMMARY

The approved resolution separates structural activation compliance from later foundation implementation work.
Structural activation compliance belongs to the phase-model promotion checkpoint.
Foundation Step 2, if later created, can only be work inside an already compliant phase box.

The target phase model is not active until the foundation phase has been normalized into the target structural inventory.
No active target phase may be structurally non-compliant.

## OPTIONS

- Allow target activation before `phase0-foundation` is structurally compliant and clean it up in Foundation Step 2.
- Remove Foundation Step 2 entirely.
- Require structural activation compliance during the promotion checkpoint, while allowing later Foundation Step 2 work inside the compliant box.

## DECISION

The agreed target phase-model rules are:

- target activation and foundation normalization are separate concepts
- structural activation compliance is part of the phase-model promotion checkpoint
- the target phase model is not active until `phases/phase0-foundation/` is normalized into a compliant promoted phase box
- no phase may be active under the target model while structurally non-compliant
- the promotion checkpoint must create or normalize `phases/phase0-foundation/` into full target structural shape before routing may select it as active
- that full target structural shape includes at minimum:
  - `CONTRACT.md`
  - `WORKPLAN.md`
  - `OPEN-ISSUES.md`
  - `steps/`
  - the active first step box under `steps/stepNN-<slug>/`
  - that step box's `CONTRACT.md`
  - that step box's `OPEN-ISSUES.md`
- Foundation Step 2 cannot mean making the foundation phase structurally valid
- any later Foundation Step 2 is foundation implementation or governance work inside the already compliant foundation phase box
- valid later Foundation Step 2 work may include migrating remaining bootstrap semantics, freeze-reviewing remaining support docs, or implementing later governance scripts if those remain in scope

This decision resolves the activation-versus-normalization finding without allowing a non-compliant active target phase.

## APPROVAL

EXPLICIT
