# PHASE-MODEL-DECISIONS-FOLDER-CONTRACT-SUPERSESSION

## CONTEXT

The second review pass on `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` raised a pushback that the target model still conflicted with current frozen bootstrap truth around the decisions folder contract.
The draft already routed future agents through `context/decisions/INDEX.md`, but current frozen bootstrap truth in `CONTEXT.md` and `context/decisions/README.md` still says that `context/decisions/` holds frozen decisions only.

## OPTIONS

- Drop `context/decisions/INDEX.md` and keep decision curation inside routing or handoff.
- Keep `context/decisions/INDEX.md`, but let agents or scripts infer an exception to the current folder contract.
- Keep `context/decisions/INDEX.md` and explicitly define a governed contract supersession at phase-model promotion time.

## DECISION

The agreed target phase-model rules are:

- the target phase model keeps `context/decisions/INDEX.md` as the curated decision-read surface
- in the target phase model, `context/decisions/` contains only frozen decision files plus the canonical support file `INDEX.md`
- `context/decisions/INDEX.md` is a governed support file, not a frozen decision entry, and therefore does not use the decision-entry contract of `CONTEXT`, `OPTIONS`, `DECISION`, and `APPROVAL`
- until the phase-model promotion checkpoint, the current bootstrap contract that `context/decisions/` holds frozen decisions only remains authoritative
- at the phase-model promotion checkpoint, the decisions-folder contract is explicitly superseded so that `context/decisions/` becomes `frozen decisions plus the canonical support file INDEX.md`
- that same promotion checkpoint must create or update `context/decisions/INDEX.md`, update `phases/ROUTING.md` to point to it, update `CONTEXT.md`, update `context/decisions/README.md`, and remove any requirement that global `context/HANDOFF.md` curate decision membership
- decision-index routing must not be activated in isolation from that broader promotion checkpoint

This decision keeps the boxed decision-index model while preventing the target phase model from contradicting the current bootstrap contract during transition.

## APPROVAL

EXPLICIT
