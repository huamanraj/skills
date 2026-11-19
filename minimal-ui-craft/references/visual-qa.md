# Browser Rendering & Visual QA Protocol

Read during Stage 7 (render, inspect, refine) of the pipeline in SKILL.md.

An agent can satisfy every checklist item and still ship an ugly page. CSS that looks correct in source routinely renders wrong: misaligned rails, clipped text, collapsed grids, invisible contrast. Visual verification against actual rendered output is mandatory, not optional.

## 1. The render-inspect-refine loop

1. Render the completed interface in a real browser when one is available (headless Chromium, a cloud browser, a local dev server screenshot). If no rendering tool exists in the environment, say so explicitly instead of claiming the design was verified.
2. Capture screenshots at 375px, 768px, and 1440px viewport widths.
3. Inspect alignment, text wrapping, hierarchy, spacing, image cropping, contrast, and overall visual balance at each width.
4. Name the three most noticeable visual problems. Write them down before touching code.
5. Fix those three problems before refining any tiny details. Biggest defects first, polish last.
6. Repeat the loop until no major layout or visual defects remain.
7. Exercise the non-default states: loading, empty, error, hover, focus, and at least one async update, not just the happy-path screen.

## 2. Composition-level checks

During inspection, ask of the whole page, not just its parts:

- Does the interface feel repetitive (the same card grid in every section)?
- Are elements boxed in unnecessarily? Apply the decoration removal test from `page-composition.md`.
- Does each section have one clear focal point?
- Does the page still hold together with real content lengths swapped in (long names, empty lists, three-line headlines)?

## 3. Implementation precision

Small rendering details separate shipped work from demos:

- **Device-pixel rendering:** hairline 1px borders must render crisply on high-DPI screens; avoid fractional-pixel positions on sharp edges. Verify at least once on a 2x display or with device emulation.
- **Font loading:** use `font-display: swap` (or `optional`), preload the primary face, and pick metric-compatible fallbacks so the swap does not reflow the page. Never let invisible-text blocking hide content.
- **CSS tokens:** values live in custom properties (`--surface-1`, `--space-4`, `--radius-card`), not scattered literals, so polarity and brand changes stay single-source.
- **Layout stability:** images and async regions reserve their final space (`aspect-ratio`, min-heights, skeletons); no cumulative layout shift while loading.
- **Browser testing:** verify in the engine the user actually has, plus one more (Chromium and WebKit/Firefox). Check the features you used (container queries, `:focus-visible`, `text-wrap`) against real support, and provide fallbacks where support is partial.

## 4. Evidence

When reporting that a UI is done, attach or reference the screenshots inspected, name what was checked, and list any state or breakpoint left unverified. "Looks correct" without rendered evidence is an unverified claim.
