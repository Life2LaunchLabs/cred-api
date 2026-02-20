# Org Members

An **OrgMember** record links a `User` to an `Org` with a specific role and status. This is the staff side of org membership — distinct from `OrgLearner` which tracks people enrolled to earn credentials.

## What it represents

When a user is invited to (or joins) an org as staff, an `OrgMember` record is created. It carries the role (`owner`, `admin`, `issuer`, `viewer`), the status (`active`, `pending`, `suspended`), and timestamps.

## Why it exists

Roles are enforced at the API layer via the `x-permissions` vendor extension on each endpoint. The membership record is what the backend resolves to determine whether a requester has permission to perform an action within a given org.

## Key relationships

- `OrgMember.userId` → `User`
- `OrgMember.orgId` → `Org`
- One user can have at most one membership per org; changing role updates the existing record rather than creating a new one

## Detail shape

The `OrgMemberDetail` type (returned by list and detail endpoints) embeds the full `User` object so that the client doesn't need a second request to display member information.
