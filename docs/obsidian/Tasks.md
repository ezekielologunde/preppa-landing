---
project: preppa-landing
type: tasks
status: active
last_updated: 2026-08-22
tags: [project/preppa-landing]
---

# Tasks

No `TODO`/`FIXME` comments were found in either app's source (`apps/marketing/src`,
`apps/help/src`). Gaps below are inferred from the README's own disclaimers and from the
codebase's current state, not from in-code markers.

## Known gaps (from README disclaimers)

- **Legal review needed**: `/legal/terms`, `/legal/privacy` (and the Cook Agreement by the
  same precedent) are explicitly flagged as drafted templates, not reviewed legal advice —
  get them reviewed by a lawyer before relying on them. See [[Decisions]].
- **Manual sync risk**: `apps/help/src/app/legal/cook-agreement/page.tsx` must be kept
  manually in sync with `preppa-app/src/lib/cookAgreement.ts` — no automated check exists
  for drift between the two repos.
- **Manual sync risk**: brand tokens (`globals.css`) are duplicated between
  `apps/marketing` and `apps/help` and must be kept in sync by hand if the brand changes.

## Inferred gaps (no evidence of the opposite in the codebase)

- No automated tests in either app.
- No CI configuration found in the repo (no `.github/workflows` observed) — deploys rely on
  Vercel's Git integration per the README's manual one-time setup.
- No CMS or content-management layer — all marketing/help copy is hardcoded in components,
  so any copy change requires a code change and redeploy.

See [[Project]] and [[Architecture]] for context.
