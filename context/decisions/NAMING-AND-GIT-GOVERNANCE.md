# NAMING-AND-GIT-GOVERNANCE

## CONTEXT

The repo needed explicit conventions for markdown file naming and for how repo truth is saved so later agents do not improvise these rules.

## OPTIONS

- Allow mixed markdown filename casing and ad hoc commit behavior.
- Freeze a governed entry-file naming rule and explicit git hygiene rules for repo-truth changes.

## DECISION

Governed created markdown entry files must use:
- `UPPERCASE-WITH-HYPHENS.md`

Fixed canonical repo surfaces may use established names defined by repo truth.

When humans refer to `adf` or `ADF` in discussion or folder references, the terms are interchangeable when the meaning is clear from context.

Git governance for repo-truth changes is:
- every logical repo-truth checkpoint must end with a commit
- commit messages must be descriptive enough that a reader can understand what changed and why without opening the diff
- the working tree must return to clean at each checkpoint and at session closeout
- push happens at stable checkpoints or when the CEO explicitly asks for it

## APPROVAL

EXPLICIT
