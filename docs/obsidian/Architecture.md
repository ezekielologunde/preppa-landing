---
project: preppa-landing
type: architecture
status: active
last_updated: 2026-08-22
tags: [project/preppa-landing]
---

# Architecture

See [[Project]] for the top-level "two apps, one repo, no monorepo tooling" summary — this
note covers the structure of each app.

## Repo layout

```
preppa-landing/
├── README.md              # Vercel setup + local dev instructions for both apps
├── apps/
│   ├── marketing/          # preppa.live
│   │   └── src/
│   │       ├── app/
│   │       │   ├── layout.tsx
│   │       │   ├── page.tsx     # composes all marketing sections
│   │       │   └── globals.css
│   │       └── components/      # one component per landing-page section
│   └── help/                # help.preppa.live
│       └── src/
│           ├── app/
│           │   ├── page.tsx     # "How can we help?" index, links to guides
│           │   ├── guides/      # cook-facing how-to guides
│           │   └── legal/       # terms, privacy, cook-agreement
│           └── components/
│               └── SiteShell.tsx
```

Both apps are standard `create-next-app`-style App Router projects — no custom server, no
API routes, no middleware found in either app.

## apps/marketing

A single-page site. `src/app/page.tsx` composes an ordered list of section components:

`Nav → Hero → FoundingCohort → WhyTrust → HowItWorks → TrustSafety → MealPlans →
FoodServices → MeetPreppas → BecomePreppa → DownloadCTA → Footer`

Each section is its own component under `src/components/`. Nav links are in-page anchors
(`#how`, `#safety`, `#plans`, `#preppas`) rather than separate routes — confirms this is a
single scrolling landing page, not a multi-page marketing site.

`framer-motion` is used for scroll-triggered reveals (`Reveal.tsx`) and nav interactions.

## apps/help

A small multi-page site under `SiteShell.tsx` (shared chrome/layout):

- `/` — index page linking to the three guides and (via footer/nav, not confirmed in code
  read so far) the legal pages.
- `/guides/post-your-first-meal`, `/guides/create-a-meal-plan`, `/guides/set-up-payout` —
  cook-facing how-to content.
- `/legal/terms`, `/legal/privacy`, `/legal/cook-agreement` — legal pages. The root README
  flags these as **drafted templates, not reviewed legal advice**, and flags
  `cook-agreement/page.tsx` specifically as needing to stay in sync with
  `preppa-app/src/lib/cookAgreement.ts`.

## What's absent (and why that's expected)

No Database, Backend, or Payments notes exist in this documentation set — the codebase has
no Supabase/DB client, no API routes, no server actions, and no payment integration code.
This is a purely presentational/content site; any real backend logic (payments, auth, cook
payouts) lives in `preppa-app`, not here.

## See also

- [[Project]]
- [[Features]]
