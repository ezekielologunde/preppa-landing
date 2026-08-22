---
project: preppa-landing
type: changelog
status: active
last_updated: 2026-08-22
tags: [project/preppa-landing]
---

# Changelog

Reconstructed from `git log`. The repo currently has a single squashed initial commit.

## 2026-07-14 — Initial commit: marketing site + help/training subdomain

Commit `2bbd593` — "Preppa marketing site + help/training subdomain". Established the
repo's two-app structure in one shot:

- `apps/marketing` (preppa.live): full landing page — Nav, Hero, Founding Cohort, Why
  Trust, How It Works, Trust & Safety, Meal Plans, Food Services, Meet Preppas, Become a
  Preppa, Download CTA, Footer.
- `apps/help` (help.preppa.live): help index, three cook guides (post your first meal,
  create a meal plan, set up payout), and legal pages (Terms, Privacy, Cook Agreement).
- Root `README.md` documenting the Vercel two-project setup and local dev instructions.

## 2026-08-22 — Obsidian documentation knowledge base added

Added `docs/obsidian/` (this documentation set) and the doc-sync kit
(`.claude/skills/obsidian-sync`, `.claude/commands/sync-docs.md`, root `CLAUDE.md`). No
application code changed.

See [[Project]] for current state.
