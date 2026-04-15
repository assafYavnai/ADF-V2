# FOUNDATION-WORKPLAN-AND-APPROVAL-GATE

## CONTEXT

The repo needed a clean separation between current foundation work and later system-definition work.
The discussion focused on where the broader workplan should live and how foundation should move forward without silently widening scope.

## OPTIONS

- Keep the broader ADF-V2 workplan inside `foundation/WORKPLAN.md`.
- Move the broader downstream workplan out of foundation and reserve `foundation/WORKPLAN.md` for the foundation layer itself.
- Let foundation progress linearly without a formal completion gate.
- Use a post-freeze foundation gate to decide whether the foundation phase is complete.

## DECISION

The broader downstream workplan is moved to `system-definition/WORKPLAN.md`.
`foundation/WORKPLAN.md` is reserved for foundation work only.

Foundation uses a local work process followed by a post-freeze gate.

The gate runs after the current foundation step is frozen.
If foundation is complete enough, freeze foundation and move forward.
If it is not complete enough, define the next foundation step, complete it, freeze it, and run the gate again.

## APPROVAL

EXPLICIT
