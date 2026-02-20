# Collections

A **Collection** is a curated group of badges published by an org. Collections are the primary way credentials are organized and browsed in the LaunchCRED registry.

## What it represents

Think of a collection as a credential catalog or course bundle — e.g. "Safety Certifications" or "Professional Development". It has a name, description, cover image, and a count of badges it contains. Collections can be `published` (visible in the public registry) or unpublished (org-private drafts).

## Why it exists

Badges are granular; collections give them context and structure. Learners and external verifiers browse collections to understand what a credential program covers. Orgs use collections to group thematically related badges and present them as a coherent offering.

## Key relationships

- One collection → many `Badge` records
- `createdByOrgId` → the org that owns the collection
- `CollectionDetail` embeds `badgeSummaries` (lightweight badge list) and `CollectionStats`

## Stats

`CollectionStats` provides aggregated issuance metrics (total issuances, unique learners, completion rate) for display on the collection detail page and org dashboard.

## Registry

Published collections appear in `GET /registry/collections`, the unauthenticated public endpoint used to browse all available credentials across all orgs.
