# SYSTEM-DEFINITION-BACKLOG-NORMALIZATION

## CONTEXT

After the no-exceptions and folder-based backlog rule was agreed, the current `phases/backlog/system-definition/` candidate was reviewed as the easiest concrete normalization case.
That backlog candidate already keeps a useful `WORKPLAN.md`, but it still carried an old nested `phases/` subtree that does not fit the governed backlog model.

## OPTIONS

- Keep the nested `phases/` subtree and treat it as a tolerated backlog exception.
- Remove `system-definition` entirely from backlog.
- Keep the backlog `WORKPLAN.md`, remove the nested `phases/` subtree, and treat `system-definition/` as a folder-based backlog candidate that can later be shaped into a compliant promoted phase.

## DECISION

The agreed current repo-truth rules for `phases/backlog/system-definition/` are:

- keep the backlog `WORKPLAN.md`
- remove the nested legacy `phases/` subtree
- treat `system-definition/` as a folder-based backlog candidate under the governed backlog model
- if `system-definition` is later selected for promotion, the retained workplan may be reused if still compliant
- that later promotion checkpoint must add the missing compliant phase `CONTRACT.md` and the rest of the required promoted-phase inventory in the same logical checkpoint

This decision normalizes the current `system-definition` backlog candidate without widening it into a promoted phase before selection.

## APPROVAL

EXPLICIT
