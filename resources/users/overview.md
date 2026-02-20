# Users

A **User** represents a registered person on the LaunchCRED platform. Users exist independently of any organization — the same account can be a staff member in one org and a viewer in another.

## What it represents

A user account holds identity information (email, name, profile photo) and optional public-facing profile fields (bio, title, location, social links). All access to org-scoped resources is mediated through **memberships** (see `org-members`) or **org-learner** records.

## Why it exists

LaunchCRED is multi-tenant: many organizations share the same platform. The `User` resource is the platform-level identity that persists across orgs. When someone signs up they get a `User`; joining an org creates a linked membership or learner record but does not duplicate the user.

## Key relationships

- One user → many `OrgMember` records (one per org they belong to as staff)
- One user → many `OrgLearner` records (one per org where they are a learner)
- JWT auth tokens are scoped to a user; org-level permissions are resolved from the active org's membership at request time

## Sample credentials (dev/mock only)

The `credentials` block in `examples.json` contains the email + password that the MSW login handler accepts in development. The `primaryUser` is the profile returned after a successful login.
