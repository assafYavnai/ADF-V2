# AGENT-BOOTSTRAP-ROUTING

## CONTEXT

Foundation Step 1 required a bootstrap path so new agents enter the repo through the foundation and context docs instead of widening scope or guessing current truth.

## OPTIONS

- Let each agent infer its own startup path from the repo.
- Create a mandatory `AGENTS.md` bootstrap order and use tool-specific stubs that redirect back to it.

## DECISION

`AGENTS.md` is the primary bootstrap file.
Before doing substantive work, agents must read the foundation-first order defined there.
After reading `context/HANDOFF.md`, agents must also read the required decision files listed in that handoff.

`CLAUDE.md` and `GEMINI.md` are minimal stubs that say:
- read `AGENTS.md` if it exists
- follow links

## APPROVAL

EXPLICIT
