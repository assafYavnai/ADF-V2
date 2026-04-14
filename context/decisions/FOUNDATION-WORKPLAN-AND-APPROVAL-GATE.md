# FOUNDATION-WORKPLAN-AND-APPROVAL-GATE

## CONTEXT

The repo needed a clean separation between current foundation work and later system-definition work.
The discussion focused on where the broader workplan should live and how foundation should move forward without silently widening scope.

## OPTIONS

- Keep the broader ADF-V2 workplan inside `foundation/WORKPLAN.md`.
- Move the broader downstream workplan out of foundation and reserve `foundation/WORKPLAN.md` for the foundation layer itself.
- Let foundation progress linearly without a formal completion gate.
- Make foundation completion an explicit approval gate that loops until the CEO decides the layer is complete.

## DECISION

The broader downstream workplan is moved to `system-definition/WORKPLAN.md`.
`foundation/WORKPLAN.md` is reserved for foundation work only.

Foundation is governed by:
- Foundation Step 1: define the foundation framework itself
- Foundation Step 2: approval gate

The approval gate rule is:
- if foundation is complete enough, freeze and approve it
- if it is not complete enough, define the next foundation step, complete it, and return to the gate

## APPROVAL

EXPLICIT
