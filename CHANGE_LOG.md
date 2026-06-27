# Change Log

## 2026-06-27 — Self-hosted fonts + GitHub Pages deploy workflow

**Summary:** Removed the Google Fonts dependency (page now makes zero external requests)
and added an automated GitHub Pages deployment.

**Files:**
- `fonts/HankenGrotesk-latin.woff2`, `fonts/Inter-latin.woff2` — self-hosted variable
  fonts (latin subset, full weight axis in a single file each)
- `index.html` — replaced Google Fonts `<link>`/preconnects with local `@font-face`
  rules using variable weight ranges (`400 800` / `300 600`)
- `.github/workflows/deploy.yml` — deploys repo root to GitHub Pages on push to `main`
  (configure-pages with `enablement: true`, upload-pages-artifact, deploy-pages)

**Validation:** woff2 signatures verified; visual QA in Launch preview.
**Status:** Fonts complete. Pages deploy blocked — see note below.

**Pages note:** GitHub Pages is not available for private repos on this account's plan.
Workflow set to manual-only (`workflow_dispatch`) so it no longer fails on each push.
To deploy: make the repo public (or upgrade), then re-enable the `push` trigger.

---

## 2026-06-27 — Initial commit: Farther Focus Team landing page for Barings

**Summary:** Single-file marketing landing page (`index.html`) presenting the Farther
Focus Team's wealth-strategy capabilities to Barings professionals, modeled on
farther.com/solutions/att and styled to the live farther.com/team/focus-team brand.

**Files:**
- `index.html` — full landing page (HTML + embedded CSS + vanilla JS, self-contained)
- `PLAN_LOG.md` — task planning history (v1 → v4)
- `TODO.md` — outstanding follow-ups
- `CHANGE_LOG.md` — this file
- `.gitignore`

**Build history (see PLAN_LOG.md for detail):**
- v1: Initial AT&T-style page for Barings employees
- v2: HNW reframe (tax deferral / estate / carry) + wow-factor interactivity
- v3: Applied real Farther brand palette + cues from farther.com/team/focus-team source
  (cream/steel-blue/charcoal, Hanken Grotesk, wave dividers, accent bars)
- v4: Dynamic pass inspired by gunboat.com + cognacgodet.com — smooth scroll, custom
  magnetic cursor, theme-aware nav, kinetic hero reveal, parallax watermarks, marquee
- v4.1: Replaced Lenis CDN with self-contained inline smooth-scroll (no runtime deps)

**Validation:** Visual QA in Launch preview. No build/lint/test pipeline (static HTML).

**Status:** Complete — page renders and is interactive.

**Known follow-ups (TODO.md):** wire booking links to real Calendly/Farther URL,
compliance review of benefit claims, confirm Barings/MassMutual plan specifics,
optional self-hosted fonts for zero external requests.

**Issues:** None blocking. Google Fonts is the only external request (graceful fallback).
