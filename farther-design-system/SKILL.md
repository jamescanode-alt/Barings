# Farther design system — usage skill

How to design _for Farther_ using this system.

## Starter checklist (every new file)

1. `<link rel="stylesheet" href="/colors_and_type.css">` — brings in tokens, font stacks, and type classes.
2. Set the canvas to `var(--surface-canvas)` (warm Limestone) unless you have a reason to go dark.
3. Use `--font-display` for hero numerals + headlines, `--font-sans` for body + UI.
4. Pull color from the semantic tokens (`--fg-primary`, `--surface-card`, …) before reaching into the raw scales.

## Color rules of thumb

| Situation | Token |
|---|---|
| Page background | `--surface-canvas` (Limestone 50) |
| Cards, inputs (light) | `--surface-card` (white) |
| Dark hero / footer / advisor rail | `--surface-inverse` (Charcoal 900) |
| Body text on light | `--fg-primary` |
| Brand CTAs / primary buttons | `--steel-700` (wordmark blue) |
| Positive data (aqua) | `--status-positive` |
| Negative data (pomegranate) | `--status-negative` |
| Conceptual diagrams / "Reserved" moments | `--bronze-400` — **use sparingly**, most reserved color |

**Do:** let Limestone breathe. **Don't:** tint Bronze large surfaces or mix >2 blues in one layout.

## Typography rules

- Headlines & hero numerals → `--font-display` (Arizona Text / Fraunces substitute), weight 300 for hero, 400 for H2/H3, italic for emotional emphasis (`<em>` inside headline).
- Body & UI → `--font-sans` (Fakt Pro / Inter substitute), weight 400 body, 500 CTAs.
- Eyebrows → `.f-eyebrow` class. Always pair with a bronze bullet dot for section opens.
- Numerics → use `.f-num-*` or apply `.tnum` — tabular figures only for financial data.

Never use Garamond or Avenir on-screen — those are the internal "house" fonts, reserved for documents.

## Components — what to reach for

- **Buttons:** primary = Steel 700 pill, secondary = charcoal outline, ghost = text + hover wash. Pill shape always.
- **Cards:** 12–16px radius, white or glass, 1px Limestone-200 hairline, shadow-2/3 for elevation.
- **Charts:** stacked columns use Granite → Steel → Clay; donuts use navy family; accent wins/losses with Aqua/Pomegranate.
- **Badges & eyebrows:** 9999px radius; bulleted eyebrows for section opens.

## Voice & tone

Visionary not idealistic · precise not cold · candid not combative · accessible not simplistic. See `preview/tone-of-voice.html` for copy examples.

## Motion

- Use `--ease-wave` for brand moments (hero, entrance of a KPI, "Waves of Wealth" moves).
- `--dur-quick` for hover/focus, `--dur-base` for card entrances, `--dur-slow` for page-level choreography.

## Assets on hand

- `assets/logos/` — wordmark navy, cream, IW lockup, symbol
- `assets/icons/` — 16 brand F-symbol SVG variants (decorative only)
- UI icons → Lucide at stroke-width 1.5, rounded caps. Steel for UI chrome, Bronze for conceptual diagrams.
- `assets/chart-samples/` — reference renders from the guidelines

## When something is missing

- No photograph? Use a gradient built from the Limestone/Clay scales at 160° — reads as "warm portraiture."
- No real advisor headshot? Initials on a Steel-700 circle.
- Unsure which blue? Default to **Steel** — it's the wordmark lock color.
