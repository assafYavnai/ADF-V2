# ADF-V2 Foundation

## Why ADF-V2 exists

ADF-V2 is a full restart.

We are creating it because ADF v1 taught us important lessons, but the repo, architecture, and accumulated operating context became too heavy to keep using as the place where first-principles v2 decisions are made.

The goal of ADF-V2 is not to deny the work done in v1.
The goal is to keep the lessons, drop the drift, and create a clean place where the foundation can be frozen clearly.

## What we learned from ADF-V1

ADF-V1 proved several important ideas:
- the user should stay in the CEO role
- the system must carry intent into execution without losing the plot
- durable state, governance, and operating discipline matter
- Phase 1 should focus on building the first real startup that can shape work and deliver implementation

ADF-V1 also exposed real problems:
- too many competing truth surfaces accumulated in one repo
- architectural thinking, implementation work, generated artifacts, operating logs, and agent residue all mixed together
- agents were repeatedly influenced by broad historical context instead of a small active source of truth
- COO-centered and other inherited framings kept reappearing even when we were trying to define a thinner v2 model
- Brain and other support tooling made it too easy to depend on old context instead of freezing new truth directly in the repo

## Why we created a new repository

We are creating a new repository because the cleanest way to avoid endless drift is to stop asking agents to reason inside the full historical weight of v1.

This new repo exists to:
- reduce context surface area
- prevent accidental inheritance from v1
- keep active truth small, explicit, and reviewable
- let us freeze the foundation before migration or implementation

ADF-V1 remains valuable as a reference repository.
It is the place to look for lessons, candidate carry-over ideas, and evidence of what worked or failed.
It is not the place where ADF-V2 foundation truth should be authored.

## Context policy for ADF-V2 right now

At the start of ADF-V2, context is saved manually in the repository.

For now:
- no Brain is treated as the active source of truth
- no external memory tool is treated as authority
- no broad historical context should override what is explicitly frozen in this repo

The repo itself is the truth surface.
If something matters, it should be written here clearly.

## What must be frozen first

Before migration from v1 or implementation of v2, we need to freeze the foundation.

The first foundation layers are:
- vision
- mission statement
- phase 1

After that, we expect to define:
- the roles of CEO, CTO, and DEV
- the expectations and rules for those roles
- the boxed building blocks ADF-V2 will be built from
- the workflows between CEO and CTO
- the workflows between CTO and DEV

Only after those layers are clear should we continue decomposing the system toward implementation.

## What this repo is for right now

This repo is the clean room for ADF-V2 foundation work.

It is for:
- freezing the top-level direction
- capturing decisions in a small and explicit way
- building the minimum trusted definition of the system before code or migration starts

It is not for:
- importing v1 by default
- recreating old structure because it already exists elsewhere
- carrying broad agent residue forward
- rushing into implementation before the foundation is stable

## Relationship to ADF-V1

ADF-V1 is now a reference system.

Use it for:
- lessons
- examples
- evidence
- possible carry-over candidates later

Do not use it as:
- automatic architecture
- automatic role model
- automatic workflow definition
- automatic context authority

## Immediate operating rule

Keep ADF-V2 small.
Freeze one layer at a time.
Do not widen the system before the current layer is truly clear.
