---
project: preppa-landing
type: features
status: active
last_updated: 2026-08-22
tags: [project/preppa-landing]
---

# Features

## apps/marketing (preppa.live) — implemented

- Sticky nav with in-page anchor links (How it works, Trust & Safety, Meal Plans, For Cooks).
- Hero section.
- "Founding Cohort" section.
- "Why Trust" section.
- "How It Works" section.
- "Trust & Safety" section.
- "Meal Plans" section.
- "Food Services" section.
- "Meet Preppas" section (introduces the cooks).
- "Become a Preppa" section — cook recruitment CTA.
- "Download CTA" section — app download call to action.
- Footer.
- Scroll-reveal animations via `framer-motion` (`Reveal.tsx`).

All implemented as static content components — no forms, no data fetching, no API calls
found in the marketing app.

## apps/help (help.preppa.live) — implemented

- Index page ("How can we help?") linking to three guides and the legal pages.
- Guides:
  - Post your first meal
  - Create a meal plan
  - Set up payout
- Legal pages:
  - `/legal/terms`
  - `/legal/privacy`
  - `/legal/cook-agreement` — mirrors `preppa-app/src/lib/cookAgreement.ts` verbatim (must
    be kept in sync manually per root README).

This is the site `preppa-app`'s Profile screen links out to (help.preppa.live) for cook
training content and legal documents, per the task brief for this documentation effort —
confirms the cross-repo link between `preppa-app` and this repo's `apps/help`.

## Not present / out of scope for this repo

- No authentication, accounts, or user sessions.
- No database or backend integration (Supabase, API routes, server actions) — confirmed
  absent from both apps' `src/` trees.
- No payments integration.
- No CMS — all copy is hardcoded in components.
- No tests found in either app.

See [[Architecture]] for the "why" behind these omissions, and [[Project]] for the overall
scope of this repo relative to `preppa-app`.
