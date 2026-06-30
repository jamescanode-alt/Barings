# Plan Log

## 2026-06-30 — Rebrand landing page to Farther design standards

**Task:** Redesign `index.html` from the Barings-mirroring system (navy #002856 + green #007836, EB Garamond + Hanken Grotesk) to the **full Farther identity** per `FARTHER_DESIGN_SYSTEM.md` and `farther-design-system/colors_and_type.css`.

**Decisions (confirmed with user):**
- Direction: **Full Farther identity** — Limestone 50 canvas, Charcoal 900 text, Steel Blue 700 brand lock; Granite/Steel deep blues for dark sections; Aqua 500 / Pomegranate 500 for positive/negative data states only.
- Signature motif: **Waves of Wealth** — replace dot-matrix halftone + guilloche rosette with self-hosted generated SVG wave bands (steel/granite resolving to clay). Preserve zero-external-request architecture.
- Type: ABC Arizona Text (Light) for headlines/titles/numerals; Fakt Pro for body/UI/eyebrows/CTAs.

**Files:**
- `fonts/` — add ABC Arizona Text + Fakt Pro (self-hosted from kit).
- `index.html` — full re-skin: @font-face, :root tokens, all section colors, hero/creed/cta motif, JS motif generator.

**Preserve:** all copy, structure, interactions (FAQ, assessment, count-up, nav theme inversion), accessibility, compliance disclaimers, zero external requests.

**Risks:** Fakt ships as OTF only (heavier than woff2); keep weights lean. Verify contrast + responsive collapse in preview before declaring done.

**Next steps:** copy fonts → rewrite index.html → verify desktop+mobile in preview → update TODO/CHANGE_LOG.

---

## 2026-06-27 — Build Barings Focus Team Website

**Task:** Create a landing page for Farther's Focus Team targeted at Barings employees, modeled on farther.com/solutions/att.

**Objective:** Convert Barings employees into Farther wealth advisory clients by showcasing the Focus Team's expertise in retirement planning for finance professionals.

**Files to create:**
- `index.html` — Main landing page
- `PLAN_LOG.md` — This file
- `CHANGE_LOG.md` — Post-push
- `TODO.md` — Follow-ups

**Key design decisions:**
- Farther brand colors (dark navy, white, clean modern typography)
- Barings employee context: finance professionals, MassMutual parent benefits, high income, sophisticated investors
- Mirror AT&T page structure: hero → myths → services → how we help → team → CTA
- Single-file HTML with embedded CSS for portability

**Risks:**
- Need to be accurate about Barings/MassMutual benefit specifics — using general finance professional framing where uncertain

**Next steps:** Build index.html, validate in browser

---

## 2026-06-27 — v2: HNW Reframe + Luxury Redesign + Wow-Factor Interactivity

**Task:** Critical review + rebuild. Reframe from generic "retirement" to HNW wealth
protection / tax deferral / estate strategy. Elevate palette to luxury. Add interactive
floating graphics behind text.

**Critical findings driving the rebuild:**
1. HOOK — "Retirement Planning" framing is too narrow/late-career. Barings pros are HNW
   ($300K–$2M+ earners) wanting income deferral, estate/generational transfer, concentration/
   carry risk, advanced tax. New hook plays on the irony: they manage institutional capital
   but neglect their own.
2. PALETTE — muddy gold (#c9a84c) + navy reads "old bank," not modern luxury. Moving to
   near-black base, refined champagne-gold gradient, deep emerald accent (nod to Barings green).
3. EMOJI ICONS — biggest luxury-killer. Replacing all with thin stroked inline SVG line icons.
4. NO WOW FACTOR — static. Adding: canvas gold particle constellation, drifting blurred
   gradient orbs, cursor-follow glow, scroll-reveal, animated stat counters, glassmorphic cards.
5. TYPOGRAPHY — adding Cormorant Garamond serif display for headline elegance.

**Compliance note:** Avoiding specific legislative/exemption figures (date is 2026, beyond
verifiable knowledge). Estate/tax claims kept strategic/general — flagged in TODO for review.

**Files:** index.html (full rewrite)

---

## 2026-06-27 — v3: Apply real Farther brand (from farther.com/team/focus-team source)

**Task:** Align to Farther's actual brand palette + design cues, pulled from the live page's HTML/CSS.

**Extracted from source:**
- Palette: cream `#F8F4F0`/`#F2EAE2` (dominant bg), ink/charcoal `#1d2b36`, steel blue
  `#557A89` (primary accent — their CSS names sections "background-color-steel"), steel-lt
  `#6f8f99`, electric cobalt `#4d65ff` (interactive/focus accent), teal/jade `#3cc1d3`,
  pale blue `#b6d0ed`, clay `#885546`, text grays `#333`/`#4f4f4f`.
- Fonts: Founders Grotesk (display) + Fakt Blond (body) — both SANS-SERIF.
- Design cues: wave dividers between sections, short colored "spacer" accent bars
  (is-jade/is-kiwi/is-navy), ~8px radii, warm light-dominant aesthetic, 3-step process.

**Applied:**
- Replaced sage-green palette → steel blue + electric blue + teal on warm cream.
- Replaced Cormorant serif → Hanken Grotesk (Founders substitute) + Inter (Fakt substitute).
- Cream-dominant section rhythm (was navy-dominant); steel-blue + charcoal dark sections.
- Added SVG wave dividers at section transitions; teal/electric accent bars under kickers.
- Electric-blue `#4d65ff` CTAs; reduced radii; kept HNW Barings content + particle hero.

**Kept:** HNW Barings copy/structure, particle constellation, scroll-reveal, counters, FAQ.

---

## 2026-06-27 — v4: Dynamic "wow" pass (gunboat.com + cognacgodet.com cues)

**Task:** Make the site more dynamic/immersive, borrowing motion + structure from two
SiteInspire luxury sites. Keep Farther brand palette + Barings content.

**Extracted from sources:**
- Both use the SiteInspire luxury stack: smooth/inertia scroll (Locomotive), custom cursor,
  Swiper, parallax (data-scroll-speed), kinetic editorial type.
- Godet signature: scroll-driven THEME INVERSION (c-theme_trigger flips light/dark on scroll);
  oversized tagline breaking across lines; words paired with inline imagery.
- Gunboat: drag-to-explore nav, cinematic full-bleed hero.
- Their hex = WordPress defaults → NOT used. Farther palette retained.

**Applied (motion/structure only):**
- Lenis smooth/inertia scroll (CDN, guarded; reduced-motion + anchor handling).
- Custom magnetic cursor (dot + lerp ring, grows on interactive hover) — hover devices only.
- Magnetic buttons (CTA pulls toward cursor).
- Theme-aware nav that inverts light/dark by the section behind it (Godet theme-trigger nod).
- Hero line-mask reveal (kinetic type) + staggered hero entrance on load.
- Parallax oversized watermark words drifting per section (editorial).
- Infinite marquee keyword ticker band.
- Upgraded scroll reveals. Kept particles, counters, FAQ, waves, palette, content.
