# FOUNDATION-WORKFLOW-AND-GLOBAL-FREEZE-RULE

## CONTEXT

The earlier wording treated the foundation gate too much like a step.
The governance model needed to be clarified so the local foundation work process and the global freeze rule were both explicit.

## OPTIONS

- Treat the gate as a foundation step.
- Treat the gate as a check that runs only after a step is frozen.

## DECISION

The foundation gate is a check.
It is not a step.

The local foundation work process is:
- define the current step
- implement the step
- freeze the step
- run the foundation gate after the step is frozen
- if foundation is incomplete, define the next step and continue
- if foundation is complete, freeze the foundation phase

Freeze is a global governance rule.
Any freeze requires approval from both CEO and CTO.

This applies to:
- step freeze
- phase freeze
- artifact freeze for promotion
- frozen decisions
- any other surface that is being frozen into trusted repo truth

## APPROVAL

EXPLICIT
