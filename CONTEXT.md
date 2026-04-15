# CONTEXT

Status: FROZEN

## Purpose

Context is the manual layer responsible for holding current ADF context and being updated frequently to reflect ADF state between sessions.

Its purpose is to preserve continuity, reduce drift, and make it possible for a contextless agent to continue work without relying on memory or hidden assumptions.

## Context v1 Structure

The current context structure includes:
- `context/decisions/`
- `context/artifacts/`
- `context/STATUS.md`
- `context/HANDOFF.md`
- `context/OPEN-ISSUES.md`

## Workplan And Step Tracking

The actual steps are defined in:
- `foundation/WORKPLAN.md`

The rule for current and next is:
- `context/HANDOFF.md` is the primary current-state authority
- `context/STATUS.md` is the thin operational mirror
- by default, `next` is the next inline step in the workplan unless the CEO explicitly says otherwise

If `context/HANDOFF.md` and `context/STATUS.md` ever diverge:
- `context/HANDOFF.md` wins
- `context/STATUS.md` must be updated immediately to match it

## Decisions

Decision means a fork-closing choice that changes current truth.

Typical examples are choices that change:
- scope
- workflow
- rules
- structure
- next-step direction
- active interpretation of repo truth

### Save rule

Frozen decisions must be saved automatically by the agent when a real decision is made and explicitly approved by the CEO.

The rule is:
- if discussion reaches a fork in the road and options are presented
- and the CEO responds with another question, discussion continues
- and the CEO responds with a decision, the frozen decision must be saved

The CEO can also explicitly ask to save a decision.

### Frozen decision rule

`context/decisions/` holds frozen decisions only.

Frozen decisions must be:
- explicitly approved by the CEO
- saved as individual decision files
- treated as active repo truth unless later replaced by another explicit CEO-approved decision

### Implicit assumption rule

Implicit agent assumptions are not frozen decisions.

If an implicit assumption matters, it should be:
- surfaced in `context/HANDOFF.md`
- tracked in `context/OPEN-ISSUES.md` if it needs later resolution
- or turned into a real frozen decision after explicit CEO approval

### Grouping rule

Several decisions may be grouped into one entry if the discussion resulted in multiple closely related decisions in the same decision event.

### Storage

Decisions are currently saved as files under:
- `context/decisions/<DECISION-SLUG>.md`

Decision filenames must follow the governed entry-file naming rule:
- `UPPERCASE-WITH-HYPHENS.md`

### Decision file shape

Each decision file must contain:
- `CONTEXT`
  - short summary of the discussion topic
- `OPTIONS`
  - what needed to be decided
- `DECISION`
  - the actual decision made
- `APPROVAL`
  - `EXPLICIT`

Frozen decision files in `context/decisions/` do not use `IMPLICIT`.
If an implicit assumption needs to be preserved before approval, keep it out of the frozen decision ledger.

## Artifacts

Artifacts are files that were created but are not yet approved.

Draft artifacts may exist in two forms:
- in-place draft canonical files
- pre-canonical drafts under `context/artifacts/`

Example:
- a canonical file such as `CONTEXT.md` may stay in its final location while its status is still `DRAFT`
- a pre-canonical working draft may live under `context/artifacts/`

Pre-canonical artifact filenames must follow the governed entry-file naming rule:
- `UPPERCASE-WITH-HYPHENS.md`

### Freeze rule

When the agent believes an artifact is ready to freeze, it asks the CEO for freeze approval.

If the answer is:
- no: apply CEO comments and check the freeze gate again later
- yes: promote the artifact

### Promotion rule

Promotion means:
- for pre-canonical drafts stored under `context/artifacts/`
- the artifact is marked as frozen
- and it is moved to its promoted location

In-place draft canonical files do not need a move step.
They stay in place and change status from `DRAFT` to `FROZEN` after CEO approval.

### Artifact file shape

Each pre-canonical artifact stored under `context/artifacts/` should carry these fixed headings:
- `STATUS`
  - `DRAFT` or `FROZEN`
- `OWNER`
  - who currently owns the next action on the artifact
- `FREEZE-GATE`
  - whether the artifact is not ready, ready for review, or ready to freeze
- `PROMOTED-TARGET`
  - the final canonical location the artifact moves to after freeze approval

In-place canonical draft files are allowed to use a lighter contract such as:
- `Status: DRAFT`

They do not need to duplicate the full pre-canonical artifact metadata block.

## Handoff

Handoff is used to hand work off to another contextless agent.

Its purpose is to create a smooth transition from one chat session to another.

Handoff should include:
- what is going on now
- what was done
- pointers to relevant files such as workplans
- highlights from the current discussion
- important decisions
- current issues being solved

Important decisions in handoff must be carried as a curated decision-read list.
Do not make the next agent scan the full decisions folder by default.

### Handoff shape

The handoff should explicitly carry:
- discussion summary of the last session
- topics discussed
- high-level decisions made
- pointers to files created or updated in the session
- the required decision files for the current handoff
- the newly created decisions in the current session
- the older decisions the current session depends on
- current task
- current step
- next step
- open blockers or risks

### Canonical handoff

There is one canonical handoff file:
- `context/HANDOFF.md`

That canonical handoff file is also responsible for carrying the curated decision-read list the next agent actually needs.
It must not point the next agent at a growing flat decision summary as a substitute.

### Update rule

Handoff is updated under these conditions:
- automatically after a step is complete and current/next step is updated
- automatically after a frozen decision is saved
- automatically after a meaningful current-state change that the next agent would need in order to continue correctly
- explicitly when the CEO asks to update handoff in order to continue in another session

## Open Issues

Open issue means:
- a subject that came up in discussion
- requires attention, further discussion, or a decision
- but is out of scope for the current task
- or is not the right thing to handle now

It becomes an open issue and is deferred for later handling.

This is a critical context layer because it prevents ideas, suggestions, gaps, and unresolved issues from falling between the cracks across time and sessions.

### Canonical file

Open issues are tracked in:
- `context/OPEN-ISSUES.md`

### Open issue shape

Each open issue should explicitly capture:
- the issue itself
- why it was deferred
- what kind of follow-up is needed
- current status

### Update rule

Open issues must be updated frequently:
- every time something is deferred, it must be entered into the open issues list
- when the CEO explicitly asks to save something for later
- when task completion changes the status of an issue

### Closure rule

When an open issue becomes closed:
- if the closure itself creates or changes frozen repo truth, create a CEO-approved decision and remove the item from the open issues list
- if the closure is routine and does not change frozen repo truth, close it directly through `context/OPEN-ISSUES.md` and preserve any needed carry-forward context in `context/HANDOFF.md`

## Status

Status is the thin operational tracker for the current foundation state.

The canonical status file is:
- `context/STATUS.md`

### Status shape

The status file should stay thin and contain:
- current stage
- current step
- next step
- current gate state

The status file complements handoff.
Status is operational and compact.
Handoff is narrative and broader.

## Rule Ownership

`RULES.md` holds narrow cross-repo conventions such as:
- naming conventions
- file-format conventions

`CONTEXT.md` holds context governance such as:
- decision save rules
- artifact and freeze rules
- handoff rules
- open-issue rules
- git/save/push governance for repo-truth updates

## Freeze Note

This file is frozen and is active repo truth until explicitly replaced by a later CEO-approved decision.

## Git And Context Writing Rules

Every logical repo-truth checkpoint must end with a commit.

A logical repo-truth checkpoint means one coherent set of related edits that together create or update one piece of repo truth.
Do not split one coherent change across multiple uncommitted checkpoints longer than necessary.
Do not begin the next unrelated repo-truth change while the previous one is still uncommitted.

Commit messages must be descriptive enough that a reader can understand what changed and why without opening the diff.
Avoid thin one-line commit messages that force later readers to inspect files or diffs just to understand the change.

The working tree must return to clean at each checkpoint and at session closeout.

Push should not happen automatically after every commit.
Push should happen when the repo reaches a stable checkpoint such as:
- after a step is completed
- after a decision is frozen
- after an artifact is promoted
- before handoff to another session
- when the CEO explicitly asks to push

These git and save rules are part of context governance and belong here.

Context files must be written explicitly and concretely.
Do not write flat shorthand bullets that leave room for interpretation.

Write context so that a contextless agent can continue correctly without guessing:
- what changed
- why it changed
- what is current
- what is next
- what is still open
