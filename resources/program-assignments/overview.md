# Program Assignments

A **ProgramAssignment** connects a `Program` to a cohort or individual learner, activating the curriculum and tracking progress. It is the runtime instance of a program template.

## What it represents

There are two assignment types:

- **CohortProgramAssignment**: Assigns a program to an entire cohort. Contains phase-level due dates for the group.
- **LearnerProgramAssignment**: Assigns a program to an individual learner (either standalone or derived from a cohort assignment). Contains the learner's specific due dates.

When a program is assigned to a cohort, individual `LearnerProgramAssignment` records are typically created for each cohort member, referencing the `cohortAssignmentId`.

## Why it exists

Programs are templates; assignments are instances. This separation allows the same program to run multiple times with different cohorts, due dates, and learner populations, while the program definition remains unchanged.

## Progress tracking

Progress is derived at query time from:
- **BadgeProgress** records (per learner, per badge): whether a badge is `not_started`, `in_progress`, or `complete`
- **CheckpointCompletion** records (per assignment, per checkpoint): staff sign-offs with optional notes

`ProgramProgress` and `PhaseProgress` (embedded in `LearnerProgramAssignmentDetail`) summarize counts of badges earned and checkpoints signed vs. total, so the client can render progress bars without computation.

## Key relationships

- `CohortProgramAssignment` → `Cohort` + `Program`
- `LearnerProgramAssignment` → `Learner` + `Program` + optionally `CohortProgramAssignment`
- `CheckpointCompletion` → `LearnerProgramAssignment` + `Checkpoint`
- `BadgeProgress` → `Learner` + `Badge` + `Org`
