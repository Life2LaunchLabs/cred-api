# Cohorts

A **Cohort** is a named group of learners within an org. Cohorts are used to organize learners into cohesive groups for program assignment, tracking, and reporting.

## What it represents

A cohort typically represents a class, intake, or batch of learners progressing through a program together (e.g. "Fall 2025 Cohort", "Safety Training Cohort"). It has a status (`active`, `draft`, `archived`) and can have staff members assigned to supervise it.

## Why it exists

Rather than assigning programs to individual learners one by one, staff assign a program to a cohort — creating `LearnerProgramAssignment` records for every learner in that cohort at once. Cohorts also serve as the reporting unit for aggregate progress.

## Key relationships

- One cohort → many `Learner` records (membership)
- One cohort → many `CohortProgramAssignment` records (programs assigned to the group)
- `assignedStaffIds` references `OrgMember` IDs for the staff responsible for the cohort

## Statuses

| Status   | Meaning                                                  |
|----------|----------------------------------------------------------|
| active   | Actively running; learners are working through programs  |
| draft    | Being set up; not yet visible to learners                |
| archived | Completed or discontinued; read-only                     |

## Detail shape

`CohortDetail` embeds the full learner list so the client can render cohort membership without additional requests.
