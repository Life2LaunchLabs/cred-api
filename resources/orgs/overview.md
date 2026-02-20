# Orgs

An **Org** (organization) is the top-level tenant in LaunchCRED. Every badge, collection, cohort, program, and learner record is scoped to an org.

## What it represents

An org can be a company, school, training provider, or any credentialing body. It has a public profile (name, logo, about text, contact info) and an internal slug used in URL routing (`/:orgSlug/...`).

## Why it exists

LaunchCRED is a multi-tenant platform. Orgs provide the ownership and permission boundary: only members of an org with the right role can create badges, issue credentials, or manage learners within that org.

## Key relationships

- One org → many `OrgMember` records (staff with roles: owner, admin, issuer, viewer)
- One org → many `OrgLearner` records (people enrolled as learners)
- One org → many `Collection` and `Badge` resources (credential catalog)
- One org → many `Cohort` and `Program` resources (learning pathways)

## Roles

| Role    | Description                                      |
|---------|--------------------------------------------------|
| owner   | Full control, including billing and org deletion |
| admin   | Manage members, badges, programs, cohorts        |
| issuer  | Issue and revoke badges to learners              |
| viewer  | Read-only access                                 |

## Stats

`OrgStats` (served by `GET /orgs/:orgId/stats`) provides aggregate counts — total members, learners, badges, issuances — used on the dashboard overview.
