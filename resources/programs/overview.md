# Programs

A **Program** is a structured learning pathway made up of sequential **Phases**, each containing badges to earn and checkpoints to complete. Programs are the highest-level pedagogical structure in LaunchCRED.

## What it represents

A program is a template — it defines the curriculum (which badges, in what order, with what checkpoints) but is not itself tied to specific learners or dates. Programs are assigned to cohorts or individual learners via `ProgramAssignment` records, which carry the actual due dates and progress.

## Why it exists

While individual badges and collections capture discrete skills, programs provide the structured arc of a longer credential journey — e.g. "Leadership Development Track" spanning three phases over six months. Programs make it easy to deliver consistent curriculum to many cohorts, track progress holistically, and generate meaningful reports.

## Structure

```
Program
  └── Phase (ordered, e.g. Phase 1: Foundation, Phase 2: Advanced)
        ├── PhaseBadge[]   (badges from any collection the learner must earn)
        └── Checkpoint[]   (milestones signed off by staff, e.g. "Submit capstone project")
```

## Key relationships

- One program → many `Phase` records (ordered by `phase.order`)
- One phase → many `PhaseBadge` and `Checkpoint` records
- One program → many `CohortProgramAssignment` and `LearnerProgramAssignment` records
- Programs are scoped to an org (`orgId`) and have a status: `active`, `draft`, `archived`

## Checkpoints

Checkpoints are milestones that require staff sign-off (a `CheckpointCompletion` record). They complement badge earning by capturing activities that can't be automatically verified — like "attend a live Q&A" or "present strategic vision to panel".
