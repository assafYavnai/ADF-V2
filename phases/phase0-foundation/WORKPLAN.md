# Foundation Workplan

Status: ACTIVE

## Purpose

This workplan defines Foundation Step 1 and the local foundation work process.

Foundation Step 1 is only about creating the foundation framework itself.
It is not yet about defining ADF vision, mission, scope, architecture, or implementation.

## Foundation Step 1

Foundation Step 1 includes:

- define `context/artifacts`
- define `context/decisions`
- define `context/HANDOFF`
- define `context/OPEN-ISSUES`
- define the high-level phase model requirements draft in `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md`
- rewrite that draft into canonical review-ready wording
- define the steps list and the rule for marking current and next
- define high-level rules such as:
  - when to save a decision
  - when to commit
  - when to push
  - when to update handoff and open items
- update `phases/phase0-foundation/README.md`
- create `AGENTS.md`, `CLAUDE.md`, and `GEMINI.md`
- wire all foundation work into those bootstrap files

## Local Foundation Workflow

The foundation workflow is:
1. define the current foundation step
2. implement the step
3. when the step is complete, freeze the step
4. after the step is frozen, run the foundation gate

The gate is a check.
It is not a step.

## Freeze Rule

Freeze is a global governance rule.

Any freeze requires approval from both:
- CEO
- CTO

This applies to:
- step freeze
- foundation freeze
- artifact freeze for promotion
- any other surface that is being frozen into trusted repo truth

## Foundation Gate

The foundation gate runs only after the current foundation step is frozen.

Gate question:
- is foundation complete?

If yes:
- freeze the foundation phase
- foundation freeze requires approval from both CEO and CTO
- mark foundation complete
- move to the next workplan layer

If no:
- define the next foundation step
- implement it
- freeze it
- run the gate again after that step is frozen

## Current State

Current focus:
- continue Foundation Step 1 through review of the active phase-model draft artifact `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md`

Current gate status:
- not ready for approval yet

Deferred foundation-phase concerns that must survive current-step promotion are tracked in:
- `phases/phase0-foundation/OPEN-ISSUES.md`
