---
project: preppa-landing
type: overview
status: active
last_updated: 2026-08-22
tags: [project/preppa-landing]
---

# Preppa Landing

## What this is

`preppa-landing` is the marketing and public-facing web presence for **Preppa**. It is a
separate repository from `preppa-app` (the main Preppa mobile/web product, built with
Expo/React Native and Supabase). This repo has no shared build tooling with `preppa-app` —
it is plain Next.js, deployed to Vercel independently.

The repo holds **two independent Next.js apps in one repo, no monorepo tooling** — just two
sibling folders, each deployed as its own separate Vercel project pointed at a different
Root Directory:

- **`apps/marketing`** → [preppa.live](https://preppa.live) — the public marketing/landing
  site (hero, how-it-works, trust & safety, meal plans, "become a Preppa" cook recruitment,
  download CTA).
- **`apps/help`** → [help.preppa.live](https://help.preppa.live) — the help/training center:
  guides for cooks, plus the legal pages (Terms, Privacy Policy, Cook Agreement).

There is no root `package.json` — each app is installed, run, and built independently
(`cd apps/marketing && npm install && npm run dev`, same for `apps/help`).

## Relationship to preppa-app

- **`preppa-app`** is the actual product: the consumer/cook mobile & web app, with Supabase
  backend, auth, payments, ordering, etc.
- **`preppa-landing`** is *not* part of that app's codebase or build — it's the public
  website surface that links people to the app, and where standalone legal/help content
  lives that the app itself links out to (e.g. the app's Profile screen links out to
  `help.preppa.live`, which is `apps/help` in this repo).
- `apps/help/src/app/legal/cook-agreement/page.tsx` is explicitly called out (in the root
  README) as mirroring `preppa-app/src/lib/cookAgreement.ts` **verbatim** — the two must be
  kept in sync manually when either changes. This is the one piece of real content coupling
  between the two repos.

## Stack

- **Framework**: Next.js 16 (App Router), React 19, TypeScript 5.
- **Styling**: Tailwind CSS 4 (`@tailwindcss/postcss`), custom CSS tokens in
  `globals.css` per app.
- **Animation**: `framer-motion` (marketing site's scroll reveals, nav, hero).
- **Linting**: ESLint 9 + `eslint-config-next`.
- **Hosting**: Vercel, two separate projects (one per app), each with its own domain and
  Root Directory setting — documented in the root `README.md`.
- **No backend/database in this repo.** No API routes, no Supabase client, no auth, no
  payments code found here — this is a static/presentational Next.js site. See the note in
  [[Features]] about what was deliberately not documented for this reason.

## Notes

- Each app carries its own `AGENTS.md`/`CLAUDE.md` (currently just Next.js "breaking
  changes" boilerplate pointing agents at `node_modules/next/dist/docs/`) — those are
  unrelated to this Obsidian documentation set.
- Brand tokens (colors, fonts) are duplicated between
  `apps/marketing/src/app/globals.css` and `apps/help/src/app/globals.css` and must be kept
  in sync manually per the root README.

## See also

- [[Architecture]]
- [[Features]]
- [[Decisions]]
- [[Tasks]]
- [[Changelog]]
