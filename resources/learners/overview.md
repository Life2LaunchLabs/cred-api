# Learners

A **Learner** is a person enrolled in one or more orgs to earn credentials. Unlike `OrgMember` (staff), learners are the recipients of badges — the end users of the credentialing system.

## What it represents

A learner has a profile (name, email, optional bio, title, location, photo) and a stable `slug` used in URLs. Within an org they appear as `OrgLearner` records, which track enrollment status and badge progress. Across orgs, the same learner identity may be enrolled in multiple places.

## Why it exists

LaunchCRED separates *staff* (OrgMember) from *learners* because their workflows are entirely different: staff design and issue credentials, learners receive and display them. The learner resource provides the public-facing identity for credential sharing and verification.

## Key relationships

- One learner → many `OrgLearner` records (one per org they're enrolled in)
- One learner → many `BadgeProgress` records (per badge per org)
- One learner → many `LearnerProgramAssignment` records (program enrollments)
- Learners belong to `Cohort` groups within an org

## Badge progress

`BadgeProgress` tracks whether a learner has `not_started`, `in_progress`, or `complete` status on a specific badge within a specific org. This is the fine-grained record used to compute program progress.
