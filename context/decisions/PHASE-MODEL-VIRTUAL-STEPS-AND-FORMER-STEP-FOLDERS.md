# PHASE-MODEL-VIRTUAL-STEPS-AND-FORMER-STEP-FOLDERS

## CONTEXT

The second review pass on `context/artifacts/PHASE-MODEL-HIGH-LEVEL-REQUIREMENTS.md` found that the draft still did not define step numbering and step-folder identity clearly enough.
The discussion then simplified the model from first principles.
The ordered workplan list already carries planned execution order, so numbering should be used only for official instantiated execution steps.
When execution order changes after a step was instantiated, preserving the old number would make the runtime view harder for humans to follow.

## OPTIONS

- Treat step numbers as stable identities and keep them even when execution order changes.
- Renumber numbered step folders in place whenever execution order changes.
- Make listed steps virtual until instantiation, make numbered folders mean official execution order in practice, and make reordered instantiated steps lose the number and fall back to preserved former-step folders tracked by phase open issues.

## DECISION

The agreed target phase-model rules are:

- the ordered implementation step list in `WORKPLAN.md` is the canonical execution order
- listed steps are virtual until instantiation
- a step becomes an official execution step only when it is instantiated as a numbered folder
- official instantiated step folders use `stepNN-<slug>/`
- if an instantiated step's execution order is changed, it loses its number and becomes a preserved former-step folder that keeps only the original slug at the phase root
- numbered step folders therefore always represent execution order in practice
- before creating a new numbered step folder, the phase must check whether a preserved former-step folder with the same slug already exists
- if it exists, the phase must re-instantiate that preserved folder by giving it the current execution number and updating its contract if needed
- that same re-instantiation checkpoint must update the phase `OPEN-ISSUES.md` entry so the former-step record is removed or closed
- if no preserved folder exists, the phase creates a new numbered step folder with the required files
- if an instantiated step loses its number, the same checkpoint must create or update a phase `OPEN-ISSUES.md` entry that points to the preserved former-step folder
- preserved former-step folders must remain tracked until they are re-instantiated, deferred upward, or explicitly accepted as no longer needed under the phase contract and user approval
- no phase may close while a preserved former-step folder still exists without an explicit recorded disposition

This decision makes runtime behavior explicit for humans and scripts, keeps execution numbering clear, and prevents reordered step work from falling between the cracks.

## APPROVAL

EXPLICIT
