# Change Log

## 2026-06-28 - Conversion pass: reframe audience, fix metric, add diagram + micro-tool

**Summary:** Targeted conversion-oriented changes on top of the Barings-brand redesign.
Broadened the audience, corrected a misleading metric, elevated the independence
disclaimer, added time-sensitive CTAs, and made the page more skimmable with a
concept diagram and an interactive micro-assessment.

**What changed:**
- **Audience reframed** from Barings-only to senior leaders across elite asset
  management, naming Barings, Point72, and Blackstone as example firms (hero badge,
  meta tags, FAQ title). Reduces the "single-firm portal clone" / affiliation risk.
- **AUM metric fixed:** replaced the misleading $481B (Barings' AUM) with **$815M**,
  labeled "Client assets advised by the Farther Focus Team" + matching footnote.
- **Independence disclaimer elevated** out of the deep footer into a visible strip
  directly under the hero (shield icon), and broadened to name Barings, Point72,
  Blackstone, and MassMutual. Full legal text retained in footer.
- **Siloed vs Unified diagram:** new section with two SVG concept diagrams contrasting
  four disconnected advisors (you as the only link) against Farther's hub-and-spoke
  coordination. Makes the cost of fragmentation visual and skimmable. Replaces the
  old text/checklist "coordinate" section (checklist preserved as compact chips).
- **Micro-assessment ("Calculate your capital deferral efficiency"):** anonymous,
  fully client-side 3-slider tool (bracket / % deferred / horizon) that computes an
  efficiency score on an animated arc gauge with a tailored interpretation and a
  consultation CTA. No data saved or sent. Labeled "illustrative, not advice."
- **Time-sensitive CTAs:** new "windows" section. Q4 deferred-comp/409A election
  window, plus a year-end estate & gifting window. NOTE: the estate hook is framed
  around the annual gift-exclusion / trust-funding reset (Jan 1), NOT an "exemption
  sunset" - the TCJA exemption was made permanent by 2025 legislation, so a sunset
  claim would be inaccurate as of 2026.

**Validation:** visual QA in Launch preview (desktop 1280 + mobile 375); assessment
logic exercised across slider extremes; all new grids collapse to single column;
0 em/en-dashes; eyebrow count 3 (within budget); Impeccable hook clean before the
6-edit cap.
**Status:** Complete.

**Follow-up refinements (same day):**
- Replaced the pill "chips" under the diagram (read as buttons, off-aesthetic) with a
  single integrated summary line using hairline rule + navy keyword emphasis.
- Moved the "Two windows" urgency section up from position 11 to directly after the
  Siloed-vs-Unified diagram (~40% scroll vs ~85%), so time-sensitive hooks reach
  skimming executives sooner. Flipped Capabilities to a white background to preserve
  light/dark section alternation after the move.

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
