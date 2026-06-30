# Farther Design System Integration

The Farther Design profile is now part of Farther Compass.

## Canonical Source

- Full imported source kit: `docs/farther-design-system/`
- Source README: `docs/farther-design-system/README.md`
- Source skill guidance: `docs/farther-design-system/SKILL.md`
- Extracted research: `docs/farther-design-system/research/`
- Original uploaded brand files: `docs/farther-design-system/uploads/`

## Runtime Assets

The platform app exposes runtime-ready design assets from:

- CSS tokens and type classes: `/design-system/colors_and_type.css`
- Fonts: `/design-system/fonts/`
- Logos, symbols, waves, chart references: `/design-system/assets/`
- HTML previews, UI kits, and deck references: `/design-system/preview/`, `/design-system/ui_kits/`, `/design-system/slides/`

`apps/platform-web/src/app/layout.tsx` loads the design-system stylesheet globally.
`apps/platform-web/src/lib/theme.ts` mirrors the core tokens for TypeScript-driven inline styles and shared components.

## Active Design Rules

- Category language is Intelligent Wealth Management.
- Product language is Intelligent Wealth Platform.
- Voice is proactive, precise, and empowering.
- Use sentence case for interface copy and headings.
- Use ABC Arizona Text for headlines, titles, and hero numerals.
- Use Fakt Pro for body, UI, eyebrows, controls, and CTA text.
- Use Limestone 50 as the default canvas, Charcoal 900 for primary text and dark sections, and Steel Blue 700 as the brand lock color.
- Use White as a secondary card or clarity surface, not as the default page canvas.
- Avoid pure black and purple in user-facing UI.
- Use Bronze sparingly for reserved brand moments and conceptual diagrams.
- Use Aqua/Pomegranate only for positive/negative data states.
- Prefer flat surfaces, hairline borders, and restrained glass effects over heavy shadows.
- Data visualization and table UI must feel like a premium consumer investing app: soft product cards, clean hierarchy, compact labels, quiet trends, polished holdings-style rows, and no default chart/table-library styling.
- Build reusable data components with Next.js app router patterns, Recharts as a fully customized rendering engine, and TanStack Table as a headless table engine with custom cell rendering.
- Use existing Farther tokens and color roles exactly as provided; do not invent a new chart/table palette.
- Charts must use custom card wrappers, subtle axes/gridlines, thin elegant strokes, restrained fills, rounded bars, compact legends, and custom premium tooltip overlays.
- Tables must feel like asset, holdings, allocation, model, or transaction views; avoid spreadsheet grids, harsh borders, loud badges, boxed cells, and generic admin-table chrome.
- All data states matter: loading, empty, no-data, filtered, selected, and hover states should be designed with the same care as the default state.

## Next UI Update Path

1. Replace page-level hardcoded colors with `theme.ts` or CSS variables from `/design-system/colors_and_type.css`.
2. Move pages toward Limestone canvas, white or glass cards, Steel CTAs, and Charcoal text.
3. Rework billing charts to use Granite, Steel, Smalt, Sky, Clay, Aqua, and Pomegranate according to the imported chart guidance.
4. Replace legacy logo references with assets from `/design-system/assets/logos/` where appropriate.
5. Use `docs/farther-design-system/ui_kits/advisor-app/` as the main advisor workspace reference.
6. Build and migrate charts/tables through `apps/platform-web/src/components/data-display/` primitives before adding one-off chart or table styles.
