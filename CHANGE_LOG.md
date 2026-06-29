# Change Log

## 2026-06-28 - Rebrand redesign to the Barings visual system (Impeccable + Taste skills)

**Summary:** Reviewed barings.com with Firecrawl, then redesigned `index.html` end to end so a
Barings employee reads it as peer-level and on-brand. Replaced the blue/teal "fintech" palette
and Inter/Hanken type with the actual Barings system: navy `#002856` dominant, green `#007836`
single accent, EB Garamond serif display + Hanken Grotesk sans, and the signature dot-matrix
halftone motif. Applied the Impeccable + design-taste-frontend skills throughout.

**What changed:**
- **Color:** committed navy/green system sampled from Barings' CSS (was blue `#4d65ff` / teal).
- **Type:** self-hosted EB Garamond (roman + italic) as serif display, mirroring Barings'
  serif headlines; dropped Inter (discouraged by both skills). Hanken Grotesk kept for body/UI.
- **Imagery:** generated SVG dot-matrix halftone field (Barings hero signature) in hero, mid-page
  conviction block, and CTA, plus a faint heritage guilloché (nod to Barings' 1762 lineage).
- **Removed AI-slop tells flagged by the skills:** gradient text (`background-clip:text`), custom
  cursor, infinite marquee, per-section eyebrows (7 -> 3), hero-metric template, identical card
  grids, scroll cue, and all em-dashes (banned by Taste; 0 remain).
- **Layout:** navy used as deliberate "brand blocks" (hero / one conviction / CTA / footer) over
  a clean light base; 8 sections now use distinct layout families (no repetition).
- **FAQ accordion** rebuilt on `grid-template-rows` (no layout-thrash) per Impeccable hook.
- **Copy:** rewrote to remove aphoristic-cadence repetition; $481B footnoted as *Barings'* AUM
  (not Farther's) for compliance accuracy. Disclaimer/not-affiliated statement retained.

**Validation:** Impeccable design hook clean ("no deterministic issues"); visual QA in Launch
preview at desktop (1280) and mobile (375); grid collapse confirmed; 0 em/en-dashes; no stale refs.
**Status:** Complete (not yet committed/pushed - awaiting user go-ahead).

## 2026-06-27 - Replace hero particle background with fixed premium backdrop

**Summary:** Removed the particle-constellation hero + flat color blocks (felt "cheap")
and introduced a single refined graphic that stays static while scrolling.

**What changed:**
- New `#bg-dark` fixed full-viewport backdrop: deep-navy aurora mesh + a generated
  **guilloché engraving** (layered rosette line-work — the banknote/stock-certificate
  motif; reads as wealth/security). Drawn once in JS, static.
- Dark sections (hero, FAQ, footer) made transparent to reveal the backdrop; Capabilities
  and CTA use a translucent steel veil so the graphic subtly shows through.
- Light sections (trust, myths, split, team) get a subtle fixed aurora mesh on cream
  (`.bg-light`, `background-attachment: fixed`) so they no longer feel flat.
- Removed the particle canvas, drifting orbs, and hero grid + their JS/keyframes.

**Validation:** visual QA in Launch preview; grep-confirmed no stale references.
**Status:** Complete.

---

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
