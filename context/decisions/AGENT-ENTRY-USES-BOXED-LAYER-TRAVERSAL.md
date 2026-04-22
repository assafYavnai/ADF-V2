# AGENT-ENTRY-USES-BOXED-LAYER-TRAVERSAL

## CONTEXT

Review of the latest phase-model findings exposed a flawed assumption about `AGENTS.md`.
The reviewers treated `AGENTS.md` as if it must become the phase execution router when the target phase model is promoted.
The discussion corrected that assumption and then narrowed the intended bootstrap model from first principles.

`AGENTS.md` is not the phase router.
It is the top-level agent entry funnel into the highest-level ADF boxes.
Each box owns its own internal pointers.
Agents reconstruct the current operating structure by opening each top-level box and following only the pointers provided by that box.

The discussion defined this as a boxed traversal model.
The top-level entry point should not try to hold a complete repo map, duplicate active phase routing, duplicate active step routing, or describe each layer's internals.
Instead, it should tell agents which top-level boxes exist, how to open them, and how to continue only through pointers exposed by the currently opened box.

The agreed current top-level boxes are:
- governance
- context

The governance box currently enters through `./RULES.md`.
The context box currently enters through `./CONTEXT.md`.
Future governance surfaces, such as a CTO role file, belong conceptually in the governance layer rather than becoming a new phase-routing concern.

The discussion also clarified that `CLAUDE.md` and `GEMINI.md` are static funnel stubs.
They should not change for phase routing, phase execution, context movement, or normal work changes.
They change only if an LLM-specific setting is required.

This decision defines the target implementation rule for phase-model promotion.
It does not authorize changing live bootstrap files during the current transition.
Until promotion, implementation exists only through the phase-model document.

## OPTIONS

- Keep `AGENTS.md` as a growing full-system map that lists active phase files, current tasks, and routing details.
- Make `AGENTS.md` the phase execution router and update it whenever phase routing changes.
- Make `AGENTS.md` a detailed layer map that explains each layer's internals.
- Make `AGENTS.md` a thin boxed-traversal entry funnel that lists only top-level layer entry points, with each layer owning its own sub-pointers.

## DECISION

The agreed target repo-truth rules for phase-model promotion are:

- `AGENTS.md` is the top-level entry funnel for agents working in ADF
- `AGENTS.md` must list only top-level layer entry points and traversal instructions
- `AGENTS.md` must not duplicate phase routing, step routing, current task state, or layer-internal summaries
- the current top-level layers are:
  - governance: `./RULES.md`
  - context: `./CONTEXT.md`
- agents must read the YAML list under `Layers`
- each YAML item is a top-level layer entry point
- each YAML item must contain:
  - `name`
  - `path`
- for each YAML item, agents must:
  - read `name` as the layer name
  - read `path` as the layer entry-point file
  - open that `path`
  - treat the opened file as authority for that layer
  - record the layer, its purpose, and any next pointers it provides in the agent's working structure map
  - follow only the links, pointers, and instructions provided inside that opened layer file
  - continue traversal only through pointers provided by the current opened box
- agents must not infer missing structure, scan outside the provided traversal path, or build a separate global map unless the user explicitly asks
- `AGENTS.md` changes only when a top-level layer entry point is added, removed, or renamed
- `AGENTS.md` does not change for normal phase execution, phase selection, step movement, or local context updates
- phase execution routing belongs below the context layer and is reached through the pointers exposed by the context box
- after target phase-model promotion, the context layer must point agents into `phases/ROUTING.md` for phase execution
- `CLAUDE.md` and `GEMINI.md` remain static funnel stubs unless an LLM-specific setting is required
- until the phase model is promoted, the live transition bootstrap remains in place and this model is implemented only through `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md`

The target `AGENTS.md` shape has exactly two sections:
- `Summary`
- `Layers`

`Summary` explains the boxed traversal goal, how agents must execute the `Layers` YAML entries, and the guardrail against scanning or inventing structure outside provided pointers.
`Layers` is a YAML dictionary/list of top-level layer names and path pointers.
Layer explanations and sublayer routing are owned by the layer entry files themselves, not by `AGENTS.md`.

At phase-model promotion, this decision supersedes the older `AGENT-BOOTSTRAP-ROUTING` decision only where that older decision implied that `AGENTS.md` should carry the full foundation-first read order directly.
Until promotion, the older decision remains the live transition runtime rule.

## APPROVAL

EXPLICIT
