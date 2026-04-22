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

The discussion refined the entrypoint shape in several steps:
- `AGENTS.md` should not become a long bootstrap list once the target model is promoted
- `AGENTS.md` should not be split into both `Top-Level Layers` and `Current Layers` because those are the same thing at the entrypoint
- `AGENTS.md` should not explain each layer's internals because each layer entry file owns its own executive summary and sub-pointers
- `AGENTS.md` should expose layer pointers as an explicit YAML structure, not as ambiguous prose
- each layer entry must include a path pointer so an agent does not have to guess where the layer starts
- the `Summary` section must tell agents their goal is to traverse all declared layers and populate a working structure map from the pointers they encounter
- agents must treat each YAML entry as an executable traversal instruction, not as decoration
- traversal must be top-down and recursive: open a box, read only that box's pointers, then continue only through those pointers

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
- `AGENTS.md` must not maintain a full map, index, or inventory of the repository
- `AGENTS.md` must have exactly two sections:
  - `Summary`
  - `Layers`
- `AGENTS.md` must not add a separate `Top-Level Layers`, `Current Layers`, layer-summary, phase-routing, or current-task section
- the current top-level layers are:
  - governance: `./RULES.md`
  - context: `./CONTEXT.md`
- `governance` is the layer for global ADF governance such as rules and roles
- `context` is the layer for current operating context, including the later path into phase routing
- adding a new governance surface, such as a role file, should be handled inside the governance layer unless it creates a genuinely new top-level layer
- agents must read the YAML list under `Layers`
- each YAML item is a top-level layer entry point
- each YAML item must contain:
  - `name`
  - `path`
- `path` must be an explicit repo-relative path pointer
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
- `CLAUDE.md` and `GEMINI.md` must not change for phase execution, phase selection, routing movement, context movement, or normal repo work
- until the phase model is promoted, the live transition bootstrap remains in place and this model is implemented only through `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md`

The target `AGENTS.md` shape has exactly two sections:
- `Summary`
- `Layers`

`Summary` explains the boxed traversal goal, how agents must execute the `Layers` YAML entries, and the guardrail against scanning or inventing structure outside provided pointers.
`Layers` is a YAML dictionary/list of top-level layer names and path pointers.
Layer explanations and sublayer routing are owned by the layer entry files themselves, not by `AGENTS.md`.
The intended result is that a contextless agent reconstructs the current operating structure by traversal rather than by relying on a maintained global map.

At phase-model promotion, this decision supersedes the older `AGENT-BOOTSTRAP-ROUTING` decision only where that older decision implied that `AGENTS.md` should carry the full foundation-first read order directly.
Until promotion, the older decision remains the live transition runtime rule.

## APPROVAL

EXPLICIT
