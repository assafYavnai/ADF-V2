# AGENT-ENTRY-USES-BOXED-LAYER-TRAVERSAL

## CONTEXT

Review of the latest phase-model findings exposed a flawed assumption about `AGENTS.md`.
The reviewers treated `AGENTS.md` as if it must become the phase execution router when the target phase model is promoted.
The discussion corrected that assumption.

`AGENTS.md` is not the phase router.
It is the top-level agent entry funnel into the highest-level ADF boxes.
Each box owns its own internal pointers.
Agents reconstruct the current operating structure by opening each top-level box and following only the pointers provided by that box.

The discussion also clarified that `CLAUDE.md` and `GEMINI.md` are static funnel stubs.
They should not change for phase routing, phase execution, context movement, or normal work changes.
They change only if an LLM-specific setting is required.

## OPTIONS

- Keep `AGENTS.md` as a growing full-system map that lists active phase files, current tasks, and routing details.
- Make `AGENTS.md` the phase execution router and update it whenever phase routing changes.
- Make `AGENTS.md` a thin boxed-traversal entry funnel that lists only top-level layer entry points, with each layer owning its own sub-pointers.

## DECISION

The agreed repo-truth rules are:

- `AGENTS.md` is the top-level entry funnel for agents working in ADF
- `AGENTS.md` must list only top-level layer entry points
- the current top-level layers are:
  - governance: `./RULES.md`
  - context: `./CONTEXT.md`
- agents must read the YAML list under `Layers`
- each YAML item is a top-level layer entry point
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

This decision supersedes the older `AGENT-BOOTSTRAP-ROUTING` decision only where that older decision implied that `AGENTS.md` should carry the full foundation-first read order directly.
The older decision remains valid for the narrow rule that agents enter through `AGENTS.md` and that tool-specific stubs funnel to it.

## APPROVAL

EXPLICIT
