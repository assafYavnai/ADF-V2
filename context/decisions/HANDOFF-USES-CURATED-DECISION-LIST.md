# HANDOFF-USES-CURATED-DECISION-LIST

## CONTEXT

We reviewed the first handoff test result and identified a bootstrap weakness.
A global `context/DECISIONS.md` summary surface may look useful at the beginning, but it becomes a growing decision pile that will overwhelm agents over time.

## OPTIONS

- Add a global `context/DECISIONS.md` file and require agents to read it at startup.
- Keep decisions as individual files and make `context/HANDOFF.md` carry the curated list of decision files required for the current handoff.

## DECISION

Do not introduce a global `context/DECISIONS.md` bootstrap surface.

`context/HANDOFF.md` must carry the decision list the next agent actually needs to read.
That list must include:
- the new decisions created in the current session
- older decisions that the current session relied on and that are required to understand the current state correctly

The handoff decision list is curated.
It is not a dump of every decision file in the repo.

## APPROVAL

EXPLICIT
