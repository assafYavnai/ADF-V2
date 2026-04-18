# ADF-V2 Workplan

## Purpose

This workplan defines the high-level order for creating ADF-V2 foundation.

It exists to keep the repo small, to prevent drift, and to stop agents from widening scope or creating system-defining documents without explicit CEO approval.

## Step 1 - Approve and freeze README

Owner:
- CEO

Rule:
- the current `phases/phase0-foundation/README.md` must be reviewed and explicitly approved by the CEO
- agent wording should not be trusted automatically for system-defining truth
- no later foundational document should be treated as valid before this approval happens

Purpose:
- confirm that the repo-start explanation is correct
- freeze the reason ADF-V2 exists
- freeze the immediate context policy for this repository

## Step 2 - Define the lighthouse with the CEO

Owner:
- CEO with CTO support

Hard rule:
- an agent is never allowed to create system-defining documents without CEO approval
- these documents must be created with the CEO, not for the CEO

The lighthouse layer includes:

### VISION

The lighthouse.
The enduring top truth of what ADF is trying to become and the principles every later decision must obey.

### MISSION-STATEMENT

The phased path to realize that vision.

### PHASE1

The concrete definition of the first phase in that mission.

Purpose:
- freeze the enduring direction first
- define the path second
- define the first concrete phase third

## Step 3 - High-level definitions

After the lighthouse layer is frozen, define the next high-level layer:

- roles, rules, boundaries, expectations, and responsibilities of CEO / CTO / DEV
- ADF building blocks, meaning the boxed building blocks of the system
- workflows between CEO<->CTO and CTO<->DEV

Purpose:
- define the system screenplay at a high level
- define the main characters and what each one does
- define the building pieces of the system before deeper decomposition starts
- define the main interaction flows before implementation design begins

## Sequencing rule

Do not skip layers.

The order is:
1. approve README
2. freeze lighthouse documents
3. freeze high-level definitions

Only after these are clear should ADF-V2 continue into deeper system decomposition.

## Guardrail

No migration from ADF-V1 and no implementation of ADF-V2 should begin before these layers are explicitly approved and frozen.
