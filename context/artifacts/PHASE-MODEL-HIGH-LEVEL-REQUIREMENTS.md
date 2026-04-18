## STATUS

DRAFT

## OWNER

CEO

## FREEZE-GATE

NOT READY

## PROMOTED-TARGET

`phases/PHASE-MODEL.md`

# PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS

This artifact captures the current high-level phase-model discussion.
It is a working draft only.
It does not freeze phase truth.
It is the current active working surface for this discussion inside Foundation Step 1.

## Agreed So Far

- A phase is an ADF work container governed by explicit repo contracts.
- `phases/ROUTING.md` is the only phase-system entry point for agents.
- `phases/STATUS.md` is not needed at this stage.
- `phases/` uses these top-level states:
  - `phases/ROUTING.md`
  - `phases/backlog/`
  - `phases/complete/`
  - one active promoted phase at `phases/phaseNNN-<slug>/`
- `phases/backlog/` holds unpromoted phase candidates.
- `phases/complete/` holds closed promoted phases.
- A blocked or deferred active phase does not need a separate suspended state.
- If a promoted phase is deferred, it may be demoted back to backlog.
- Promoted phase identity and execution order are different concerns.
- The promoted phase folder keeps one stable phase id in its path.
- Execution order should be carried by routing and current-state tracking, not by the folder path.
- Promoted active phase folders use `phases/phaseNNN-<slug>/`.
- Backlog candidate folders use `phases/backlog/<slug>/`.
- Completed phase folders use `phases/complete/phaseNNN-<slug>/`.
- Step folders use `stepNN-<slug>/` under the phase folder.
- Folder and file naming should use lowercase kebab-case for slugs, with zero-padded numeric ids for promoted phases and steps.
- Promotion from backlog to active phase requires a fully compliant `CONTRACT.md` and `WORKPLAN.md`.
- A phase receives its promoted phase number only when the user selects it for promotion.
- `CONTRACT.md` is created before `WORKPLAN.md`.
- `WORKPLAN.md` is derived from `CONTRACT.md` and cannot expand contract scope.
- No implementation starts until the phase workplan is frozen.
- `WORKPLAN.md` may later be unfrozen because of discoveries during implementation.
- The unfreeze and reprioritization process must be defined explicitly.
- Frozen phase scope is not allowed to be breached.
- If requested work does not fit the frozen phase purpose, outputs, or exit gate, it is out of scope unless `WORKPLAN.md` is explicitly unfrozen and revised.
- If the work still does not fit after that test, it must become a different phase candidate.
- A completed phase is moved to `phases/complete/` after the user approves the phase close gate.
- Completion may also move outputs to other destinations if that is defined in the phase contract.
- Backlog candidates may be lightweight or mature.
- A backlog candidate must have at minimum:
  - a slug-based folder under `phases/backlog/`
  - a `README.md` with explanation and context of the candidate
- Each layer has its own `OPEN-ISSUES.md`.
- Open-items scope is layered as:
  - general
  - phase
  - step
- A step cannot close while it still owns unresolved step-scoped open items unless those items are explicitly transferred forward.
- A phase cannot close while it still owns unresolved phase-scoped open items.
- To close a phase, remaining phase-scoped items must be either resolved or transferred out to backlog or general-level open items.
- A working artifact should be maintained during discussion so agreed items, open questions, and later-deferred items stay separate.

## Open Questions

- What is the final canonical promoted target for this phase-model artifact after approval?
- What is the minimum required field list for a phase `CONTRACT.md` in final wording?
- What is the minimum required field list for a phase `WORKPLAN.md`?
- What exact content must appear in `phases/ROUTING.md`?
- What is the approval rule for demoting a promoted phase back to backlog?
- What is the exact close-gate wording for a phase?
- What is the exact close-gate wording for a step?
- What is the minimum required step contract in final wording?
- What is the exact file inventory required inside a promoted phase folder?
- What is the exact file inventory required inside a step folder?

## TBD Later

- The detailed operational process for unfreezing and re-freezing `WORKPLAN.md`.
- Which kinds of workplan edits are allowed during unfreeze.
- How approvals are recorded mechanically in the repo.
- Whether later script governance should enforce routing, gates, or promotions.
- Whether `phases/PHASE-MODEL.md` remains the right canonical target after the model is finalized.
