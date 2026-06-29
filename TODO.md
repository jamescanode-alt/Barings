# TODO

## Follow-ups & Improvements

- [ ] Add real advisor headshots and bios once provided
- [ ] Confirm specific Barings/MassMutual benefit plan names (pension, deferred comp plan names) with HR/compliance for accuracy
- [ ] Wire up all "Request a consultation" CTAs (nav, hero, assessment, CTA) to the real Calendly / Farther booking link (currently the CTA section links to farther.com/contact)
- [ ] Confirm the $815M Focus Team AUM figure with compliance, and keep it current
- [ ] Confirm the deferral-efficiency tool's heuristic is acceptable to compliance (it is labeled illustrative / not advice, fully client-side); consider replacing with a vetted formula
- [ ] Optionally pipe assessment results into the booking link (e.g. prefill score) if a real booking tool is connected
- [ ] Add Google Analytics or tracking pixel if needed
- [ ] Consider adding a testimonials/social proof section once client quotes are available
- [x] Mobile QA - verified hero + collapsing grids at 375px in Launch preview (2026-06-28)
- [x] Add Open Graph meta tags for social sharing previews (og:title/description/type present)
- [ ] Accessibility audit (contrast ratios, keyboard nav, screen reader) - spot-checked AA;
      run full audit. Note: FAQ buttons now expose `aria-expanded`.
- [ ] Replace the two reference JPGs (Baring_History.jpg, "Fixed Income.jpg") - they are
      screenshots of barings.com WITH Barings nav chrome, so they cannot be embedded as assets.
      If real photography is wanted on-page, source/self-host clean architectural images
      (current build stays zero-external-request, using generated SVG motifs instead).
- [ ] Legal/compliance review of all benefit claims before publishing
- [ ] Deployment: GitHub Pages needs a public repo on the current plan. To go live,
      make the repo public (or upgrade), then re-add the `push` trigger in
      `.github/workflows/deploy.yml` (currently manual-only). Alternative: host on
      Netlify/Vercel/Railway while keeping the repo private.
