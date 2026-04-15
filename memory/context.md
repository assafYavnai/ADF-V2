The core idea

Right now the repo preserves three things fairly well:

frozen truth
current operating state
deferred items

What it does not preserve well is:

important session learnings that are not yet frozen
active assumptions that are being worked under
rejected paths that matter later
partial conclusions that are too important to lose, but not mature enough to freeze

That missing category needs its own governed surface. Right now, if it is not frozen, not deferred, and not squeezed into handoff prose, it can disappear.

The model I recommend

Think in four layers, not one.

1. Frozen truth

This is what you already have:

approved decisions
frozen canonical docs

This should stay strict, curated, and hard to change. That part of the model is good.

2. Active working context

This is the missing layer.

This should hold:

important current assumptions in use
active interpretations that are not frozen yet
paths explored and ruled out during the current work
known fragilities
unresolved but in-scope findings
important reasoning that the next agent must inherit to avoid repeating work or drifting

This is not frozen truth.
It is also not just “open issues.”
It is the current working mental model that must survive session boundaries.

3. Handoff

Handoff should stay what it is supposed to be:

concise narrative bridge
what changed
where the work stands
what to read next

But instead of trying to contain all working context itself, it should point to the active working-context surface.

4. Deferred issues

That remains OPEN-ISSUES.md.
Only things that are intentionally parked should go there.

Why this is better

Because it separates two jobs that are currently being mixed:

HANDOFF.md is trying to be both:

a readable bridge for the next agent
and the container for all non-frozen but important context

Those two goals conflict.

A good handoff is short and selective.
A full carry-forward context store is not short and not selective.

So instead of forcing one file to do both badly, split them:

handoff = bridge
working-context = deep carry-forward state
The rule that fixes the lossiness

At session end, every important piece of session context must be forced into exactly one bucket:

frozen truth
active working context
deferred issue
discarded / no longer needed

If it stays in none of those, it is not preserved.

That is the real governance rule missing today.

What not to do

I would avoid these two bad fixes:

Bad fix 1: make HANDOFF.md huge

That solves lossiness by destroying usability.
The next agent will stop reading it properly.

Bad fix 2: dump everything into decisions

That corrupts the meaning of frozen decisions and weakens governance.
Your current decision discipline is one of the strongest parts of the system. Keep it strict.

What I would add conceptually

At a high level, I would add a governed surface with a name like:

context/WORKING-CONTEXT.md
or
context/ACTIVE-CONTEXT.md

Its role would be:

carry all important non-frozen context that must survive between sessions.

Then the handoff process becomes:

update frozen decisions if a real decision happened
update open issues for anything deferred
update active working context for important non-frozen learnings
update handoff to summarize the session and point to what the next agent must read

That gives you full continuity without polluting frozen truth.

The design principle underneath all this

You need to stop thinking of handoff as a single file problem.

It is a context pipeline problem.

A robust handoff system is not:

one summary file

It is:

a set of governed sinks
plus a normalization rule
plus a deterministic read order

You already have much of the deterministic read order.
What is missing is the mandatory sink for active, non-frozen session knowledge.

My recommendation at high level:

Keep the current truth surfaces. Add one explicit active-working-context surface. Make session closeout normalize all important knowledge into the right bucket. Let handoff become the bridge, not the warehouse.