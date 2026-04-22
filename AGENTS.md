# ADF Agent Entry

## Summary

This file is the top-level entry funnel for agents working in ADF.

The agent's first goal is to reconstruct the current ADF operating structure by traversing the declared layers below.

Agents must read the YAML list under `Layers`.
Each YAML item is a top-level layer entry point.

For each YAML item:
1. Read `name` as the layer name.
2. Read `path` as the layer entry-point file.
3. Open that `path`.
4. Treat the opened file as the authority for that layer.
5. Record the layer, its purpose, and any next pointers it provides in the agent's working structure map.
6. Follow only the links, pointers, and instructions provided inside that opened layer file.
7. Continue traversal only through pointers provided by the current opened box.

ADF uses a boxed traversal model.
Each layer is a box.
Opening a box may reveal more boxes.
Agents construct the operating structure by traversing provided pointers, not by scanning the repository or inventing a global map.

**Guardrail: agents must only follow the links each layer / box provides. Do not infer missing structure, scan outside the provided traversal path, or build a separate global map unless the user explicitly asks.**

After traversal, the agent should work only inside the reconstructed structure and the user's explicit request.

## Layers

```yaml
layers:
  - name: governance
    path: ./RULES.md
  - name: context
    path: ./CONTEXT.md
```
