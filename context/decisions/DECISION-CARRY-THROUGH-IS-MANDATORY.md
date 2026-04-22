# DECISION-CARRY-THROUGH-IS-MANDATORY

## CONTEXT

During the phase-model review, a repeated failure pattern appeared.
Some approved decisions were captured at the concept level but not fully carried through into all dependent artifact sections, decision files, schemas, routing rules, gate rules, status references, and handoff wording.

That created a risk that later agents would see a decision described as fixed or integrated while a dependent file still carried stale or incomplete truth.

The discussion clarified that this is not only a local phase-model cleanup problem.
ADF needs a global governance rule that prevents agents from calling a decision implemented before all affected repo-truth surfaces have been updated or explicitly marked unchanged with reason.

## OPTIONS

- Keep carry-through as an informal agent habit.
- Add a local reminder only inside the phase-model artifact.
- Add a global rule in `RULES.md` and mirror the local application inside the phase-model artifact.

## DECISION

Approved decisions require carry-through before they may be described as integrated, fixed, closed, or implemented.

Carry-through means updating every dependent:
- artifact section
- decision file
- example
- routing rule
- gate rule
- status reference
- handoff reference
- transition rule

If a dependent surface is intentionally unchanged, the reason must be explicitly recorded.

This rule is global ADF governance and is recorded in `RULES.md`.
The phase-model artifact also carries a local application of the same rule for phase-model review and freeze-readiness work.

## APPROVAL

EXPLICIT
