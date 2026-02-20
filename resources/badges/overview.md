# Badges

A **Badge** is the fundamental credential unit in LaunchCRED. Each badge represents a specific, verifiable skill or achievement, and carries the criteria a learner must satisfy to earn it.

## What it represents

A badge has a name, description, image, and one or more `Criterion` records that define what earning it requires. Criteria can be required or optional. The badge is owned by an org (via `createdByOrgId`) and belongs to one or more `Collection` groups.

## Why it exists

Open badges (aligned with IMS Global standards) are the atomic unit of verifiable credentials. LaunchCRED issues digitally signed badge assertions that learners can share with employers or embed in portfolios. The criteria structure makes the evidence of achievement transparent and auditable.

## Key relationships

- One badge → many `Criterion` records (earning requirements)
- One badge → one or more `Collection` records (grouped into catalogs)
- `BadgeProgress` tracks per-learner, per-org completion status
- `PhaseBadge` embeds badges inside `Program` phases

## Criteria

Each `Criterion` has a human-readable `label` and an `isRequired` flag. Non-required criteria represent bonus or optional evidence that enriches the credential without blocking issuance.

## Issuance

When a learner satisfies all required criteria, a staff member (with `issuer` role or higher) can issue a badge assertion. Issued badges generate a permanent, verifiable record linked to the learner's profile.
