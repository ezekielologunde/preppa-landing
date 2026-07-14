# preppa-landing

Two independent Next.js apps, one repo — no monorepo tooling, just two sibling folders,
each deployed as its own Vercel project pointed at a different Root Directory.

- **`apps/marketing`** → [preppa.live](https://preppa.live) — the public marketing site.
- **`apps/help`** → [help.preppa.live](https://help.preppa.live) — training guides, Terms,
  Privacy Policy, and the Cook Agreement.

## Vercel setup (one-time, manual)

1. **Marketing** (`preppa.live`) — in the existing Vercel project that owns this domain,
   go to Project Settings → Git and connect it to this repository, with **Root Directory**
   set to `apps/marketing`.
2. **Help** (`help.preppa.live`) — create a new Vercel project, import this same repository,
   set **Root Directory** to `apps/help`, then attach the `help.preppa.live` domain under
   Project Settings → Domains.

Both apps build with the default Next.js settings (`next build`) — no custom build command
needed.

## Local development

```bash
cd apps/marketing && npm install && npm run dev   # http://localhost:3000
cd apps/help && npm install && npm run dev          # http://localhost:3000 (use a different port if running both)
```

## Content notes

- Brand tokens (colors, font) are duplicated between `apps/marketing/src/app/globals.css` and
  `apps/help/src/app/globals.css` — keep them in sync if the brand changes.
- `apps/help/src/app/legal/cook-agreement/page.tsx` mirrors
  `preppa-app/src/lib/cookAgreement.ts` verbatim — update both together.
- `apps/help/src/app/legal/terms` and `.../privacy` are drafted templates, **not reviewed
  legal advice** — get them reviewed by a lawyer before relying on them, same as the existing
  Cook Agreement's own disclaimer.
