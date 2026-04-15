# MANUAL-CONTEXT-STRUCTURE-AND-TRACKERS

## CONTEXT

The discussion defined what manual context means in ADF-V2 foundation and which files are canonical for continuity between sessions.

## OPTIONS

- Keep context informal and let agents improvise where current state, deferred issues, and handoff notes live.
- Define a fixed manual context structure with clear file responsibilities and a single canonical tracker for each concern.

## DECISION

Manual context v1 uses this structure:
- `context/decisions/`
- `context/artifacts/`
- `context/HANDOFF.md`
- `context/OPEN-ISSUES.md`
- `context/STATUS.md`

The canonical tracking rules are:
- the actual step list is defined in `foundation/WORKPLAN.md`
- current step and next step are defined in `context/HANDOFF.md`
- `context/STATUS.md` is the thin operational tracker
- by default, next step is the next inline step in the workplan unless the CEO explicitly says otherwise
- `context/HANDOFF.md` is the one canonical handoff file
- `context/HANDOFF.md` carries the curated decision files required for the current handoff
- `context/OPEN-ISSUES.md` is the one canonical deferred-items file

## APPROVAL

EXPLICIT
