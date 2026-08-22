---
project: preppa-landing
type: decisions
status: active
last_updated: 2026-08-22
tags: [project/preppa-landing]
---

# Decisions

## Two apps, one repo, no monorepo tooling

The marketing site and the help/training site are kept as two independent Next.js apps in
sibling folders (`apps/marketing`, `apps/help`) inside a single repo, with **no** monorepo
tooling (no Turborepo, no shared workspace `package.json`, no shared component package).
Each app is deployed as its own separate Vercel project with a distinct Root Directory
setting. Rationale (from the README): keeps deploys and domains fully independent
(`preppa.live` vs `help.preppa.live`) while still allowing shared repo history and easy
cross-reference between the two apps' content.

Trade-off accepted: brand tokens are duplicated between the two apps' `globals.css` files
and must be manually kept in sync — documented explicitly in the README rather than solved
with shared tooling.

## Legal/help content lives in its own repo, separate from preppa-app

Rather than serving help/legal content from within the `preppa-app` product itself, it's
hosted as a standalone Next.js site (`apps/help`) on its own subdomain
(`help.preppa.live`). `preppa-app` links out to it (e.g. from its Profile screen). See
[[Project]] for how this repo relates to `preppa-app`.

## Cook Agreement content is duplicated, not shared, across repos

`apps/help/src/app/legal/cook-agreement/page.tsx` intentionally mirrors
`preppa-app/src/lib/cookAgreement.ts` **verbatim** rather than the two repos sharing a
single source of truth (e.g. via a package or a fetched document). This is a manual-sync
decision, explicitly flagged as a maintenance risk in the root README.

## Legal pages are drafted templates, not reviewed legal advice

The Terms, Privacy Policy, and (by the same disclaimer precedent) Cook Agreement pages are
explicitly marked in the README as drafted templates that need lawyer review before being
relied upon — a stopgap-content decision rather than a finished legal deliverable.

See [[Tasks]] for the follow-up implied by this.
