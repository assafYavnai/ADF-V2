# NAMING-AND-OPEN-ISSUE-CLOSURE-CLARIFICATIONS

## CONTEXT

After the main context-governance cleanup, two remaining ambiguities were found:
- the markdown naming rule overstated repo reality by implying every markdown file uses the same naming pattern
- the open-issue closure rule still implied that routine issue closure must create a frozen decision

## OPTIONS

- Keep the global markdown naming claim and the always-create-a-decision closure rule.
- Narrow the naming rule to governed created entry files and narrow closure decisions to real CEO+CTO-approved truth changes only.

## DECISION

The clarified rule is:
- the `UPPERCASE-WITH-HYPHENS.md` naming rule applies to governed created entry files such as decision entries and pre-canonical artifact drafts
- fixed canonical repo surfaces may use established names defined by repo truth
- open-issue closure creates a frozen decision only when the closure itself creates or changes frozen repo truth under the global freeze rule
- routine open-issue closure is handled directly in `context/OPEN-ISSUES.md`, with any needed carry-forward context preserved in `context/HANDOFF.md`

## APPROVAL

EXPLICIT
