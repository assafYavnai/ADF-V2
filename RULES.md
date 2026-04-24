# RULES

- `adf` and `ADF` are interchangeable in human discussion and folder references when the meaning is clear from context.
- Governed created markdown entry files such as decision entries and pre-canonical artifact drafts must use `UPPERCASE-WITH-HYPHENS.md`.
- Fixed canonical repo surfaces may use established names such as `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `README.md`, `RULES.md`, `CONTEXT.md`, `HANDOFF.md`, `STATUS.md`, and `OPEN-ISSUES.md`.
- If the CEO refers to a file in a different case, the agent must still save it using the canonical name defined by repo truth.
- Governed repo structures must not rely on standing exceptions. If a structure is non-compliant, it must be normalized into the governed model in the same logical checkpoint that activates or reclassifies it.
- Approved decisions require carry-through before they may be described as integrated, fixed, closed, or implemented. Carry-through means updating every dependent artifact section, decision file, example, routing rule, gate rule, status or handoff reference, and transition rule affected by the decision, or explicitly recording why a dependent surface is unchanged.

## Boxed Builder-Reviewer Principle

ADF boxes are governed process boundaries, not only folders or files.
Each governed box must define its inputs, rules, output artifact, maturity check, failure path, and promotion or handoff behavior.

A builder box also reviews the artifact it consumes.
If the input artifact is not mature enough to create the requested output, the builder must return the gap to the owning upstream box instead of inventing missing truth or bypassing governance.

The default pipeline pattern is:
- need or pain becomes a definition input
- a builder creates the next governed artifact
- that builder validates the maturity of the previous artifact
- if validation fails, work returns to the previous box for revision
- if validation passes, the output artifact can move to its next governed box

Future scripts should implement these boxes with explicit inputs and outputs.
Scripts may enforce the boxed model but must not redefine it.
