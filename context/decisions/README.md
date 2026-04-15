# DECISIONS

This folder holds frozen decisions for ADF-V2.

Rule:
- no decision is frozen unless it is explicitly approved by both CEO and CTO
- agents must not freeze system-defining decisions by inference
- decision filenames must use the governed entry-file naming rule: `UPPERCASE-WITH-HYPHENS.md`
- each decision entry must contain `CONTEXT`, `OPTIONS`, `DECISION`, and `APPROVAL`
- save a decision when a real fork is closed and approved under the global freeze rule, or when the CEO explicitly asks to save it and the freeze approval is completed
- files in this folder hold frozen decisions only
- `APPROVAL` in this folder is `EXPLICIT`
- implicit agent assumptions do not belong in this folder until CEO and CTO explicitly approve them as real decisions
