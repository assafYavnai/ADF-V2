# Context

Status: draft

## Purpose

Context is the manual layer responsible for holding current ADF context and being updated frequently to reflect ADF state between sessions.

Its purpose is to preserve continuity, reduce drift, and make it possible for a contextless agent to continue work without relying on memory or hidden assumptions.

## Context v1 Structure

The current context structure includes:
- `context/decisions/`
- `context/artifacts/`
- `context/HANDOFF.md`
- `context/OPEN-ISSUES.md`

## Decisions

Decision means:
- an issue
- a suggestion
- a proposal
- or another discussion artifact

that ends in CEO approval or a CEO decision.

### Save rule

Decisions must be saved automatically by the agent when a real decision is made.

The rule is:
- if discussion reaches a fork in the road and options are presented
- and the CEO responds with another question, discussion continues
- and the CEO responds with a decision, the decision must be saved

The CEO can also explicitly ask to save a decision.

### Grouping rule

Several decisions may be grouped into one entry if the discussion resulted in multiple closely related decisions in the same decision event.

### Storage

Decisions are currently saved as files under:
- `context/decisions/<slug>.md`

## Artifacts

Artifacts are files that were created but are not yet approved.

Draft artifacts are saved under:
- `context/artifacts/`

Example:
- if `README.md` is still draft, it should live under `context/artifacts/README.md`

### Freeze rule

When the agent believes an artifact is ready to freeze, it asks the CEO for freeze approval.

If the answer is:
- no: apply CEO comments and check the freeze gate again later
- yes: promote the artifact

### Promotion rule

Promotion means:
- for foundation scope, where we are currently creating docs
- the artifact is marked as frozen
- and it is moved to its promoted location

Promoted artifacts are moved, not duplicated.

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

### Canonical handoff

There is one canonical handoff file:
- `context/HANDOFF.md`

### Update rule

Handoff is updated under two conditions:
- automatically after a step is complete and current/next step is updated
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

### Update rule

Open issues must be updated frequently:
- every time something is deferred, it must be entered into the open issues list
- when the CEO explicitly asks to save something for later
- when task completion changes the status of an issue

### Closure rule

When an open issue becomes closed:
- create a decision that the item was closed
- include reason and relevant context
- remove the item from the open issues list

## Draft Note

This file is a draft and should not be treated as frozen until the CEO explicitly approves it.

## Git And Context Writing Rules

Every CRUD operation that changes repo truth must end with a commit.

Commit messages must be descriptive enough that a reader can understand what changed and why without opening the diff.
Avoid thin one-line commit messages that force later readers to inspect files or diffs just to understand the change.

The working tree must stay clean at all times.

Push should not happen automatically after every commit.
Push should happen when the repo reaches a stable checkpoint such as:
- after a step is completed
- after a decision is frozen
- after an artifact is promoted
- before handoff to another session
- when the CEO explicitly asks to push

Context files must be written explicitly and concretely.
Do not write flat shorthand bullets that leave room for interpretation.

Write context so that a contextless agent can continue correctly without guessing:
- what changed
- why it changed
- what is current
- what is next
- what is still open
