---
name: minimal-ui-craft
description: Build minimal, designer-crafted user interfaces and eliminate generic "AI slop" styling. Use this skill whenever designing, building, reviewing, or restyling any web UI — dashboards, landing pages, SaaS apps, admin panels, settings screens, or individual components — especially when the user asks for a minimal, clean, premium, or designer-quality look, mentions "AI slop", or says generated UI looks generic or amateurish. The rules are theme-agnostic and adapt to any brand color, light or dark mode, and any framework (React, Tailwind, plain CSS, etc.).
---
name: minimal-ui-craft
description: Build minimal, designer-crafted user interfaces and eliminate generic "AI slop" styling. Use this skill whenever designing, building, reviewing, or restyling any web UI , dashboards, landing pages, SaaS apps, admin panels, settings screens, or individual components , especially when the user asks for a minimal, clean, premium, or designer-quality look, mentions "AI slop", or says generated UI looks generic or amateurish. The rules are theme-agnostic and adapt to any brand color, light or dark mode, and any framework (React, Tailwind, plain CSS, etc.).
---

# Minimal UI Craft

A universal, theme-agnostic UI engineering and visual design specification: the structural, optical, typographic, and lighting rules that separate designer-crafted minimalism from generic "AI slop." Apply these principles dynamically on top of any user-provided design system, brand palette, or layout spec , never hardcode a single style or color scheme.

## Core philosophy

Minimalism is not the absence of styling; it is the deliberate removal of visual friction so that proportion, typography, surface contrast, and light carry the entire hierarchy.

"AI slop" fails because it compensates for weak hierarchy with louder styling: heavy glows, saturated backgrounds, chunky drop shadows, rainbow badges, oversized radii, and emoji clutter. High-craft minimal UI achieves clarity through restraint, tonal stepping, and optical precision.

## Diagnostic matrix: slop vs. craft

| Visual Dimension | Generic "AI Slop" (Anti-Pattern) | Designer-Crafted Minimalism (Target) |
| :--- | :--- | :--- |
| **Color Usage** | Saturated gradients across backgrounds, cards, and borders simultaneously; brand color plastered on 40%+ of pixels. | Neutral-first foundation (90%+ of viewport). Brand color reserved strictly for primary actions, active signals, and focal accents. |
| **Depth & Elevation** | Single heavy, muddy black shadow (`0 10px 25px rgba(0,0,0,0.4)`) or completely flat elements with zero separation. | Layered depth combining subtle surface-luminance steps, whisper-quiet hairline borders, multi-layer ambient shadows, and directional top-edge highlights. |
| **Spacing & Rhythm** | Arbitrary vertical gaps (e.g., `13px`, `26px`, `44px`, `30px`) and misaligned container rails. | Strict adherence to a base spatial grid (`4px` / `8px`), disciplined proximity grouping, and razor-sharp vertical alignment rails. |
| **Typography** | Heavy bold weights everywhere, identical luminance for labels and values, default letter-spacing on large headings, non-tabular numbers. | Tonal hierarchy (weight + opacity + scale), tightened display tracking, crisp editorial or geometric pairings, and `tabular-nums` for all numeric data. |
| **Border Radius** | Identical large radius slapped onto both parent containers and tightly nested children, causing awkward corner pinching. | Mathematically concentric radii (`R_inner = R_outer - Padding`) scaled proportionally to element height. |
| **Badges & Counters** | Bright, glowing pill backgrounds around every status, tag, and numeric count. | Plain right-aligned muted numerals for counts; low-opacity tinted pills or `6px` status dots for semantic states. |
| **Iconography & Copy** | Emojis, exclamation marks (`+12%!!`), mixed icon libraries, inconsistent stroke weights. | Monochrome vector icons with uniform stroke weight (`1.5px` or `1.75px`), calm objective microcopy, zero UI emojis. |
| **Data Visualization** | Thick glowing bars, neon fills, loud legends, and cluttered gridlines. | Fine strokes, restrained opacity gradients, subtle axis hairlines, and crisp direct-read metrics. |

## Execution pipeline

Run this 5-stage pipeline before writing final UI code. Each stage has a reference file with the full rules , read it when you reach that stage.

### Stage 1: Ingest and derive tokens
Read the user's polarity (light, dark, or both), primary brand color, typography preference, and information density. Derive the 4-tier neutral surface ramp, 4-tier text contrast ramp, hairline border opacity, and 2-layer elevation shadows as CSS custom properties (`--surface-0` to `--surface-3`, `--text-1` to `--text-4`, `--border-subtle`, `--radius-card`, `--radius-inner`).
→ Full rules: `references/color-and-surfaces.md`

### Stage 2: Establish spatial skeleton
Lock the layout grid (4px/8px spacing scale), sidebar width (220–260px), and max content width. Verify every vertical alignment rail (sidebar logo, search input, nav headers, nav icons, page title, card grid left edge) aligns to exact grid coordinates.
→ Full rules: `references/spacing-and-layout.md`

### Stage 3: Construct typographic hierarchy
Assign font families or weights per the pairing archetype that fits the product. Apply negative tracking to headings/KPIs (≥20px), `tabular-nums` to all numeric figures, and tonal contrast to compound titles and metric-unit pairs.
→ Full rules: `references/typography.md`

### Stage 4: Craft surfaces and micro-depth
Apply surface luminance stepping + 1px hairline borders first; add feathered multi-layer shadows only to elements that genuinely float. Apply specular top-edge highlights on elevated dark surfaces and dark primary buttons. Verify concentric radii on every nested element.
→ Full rules: `references/color-and-surfaces.md` (depth & lighting), `references/spacing-and-layout.md` (radius math)

### Stage 5: Anti-slop polish pass (mandatory self-audit)
Audit every component against the checklist below and strip excess decoration. Component-level patterns (navigation, cards, segmented controls, charts, icons, microcopy) are in `references/components-and-icons.md`.

## The 12-point anti-slop checklist

Verify all 12 checkpoints before considering a minimal UI complete:

- [ ] **No Neon Soup:** At least 85–90% of the viewport is calm neutral surfaces.
- [ ] **No Muddy Shadows:** All drop shadows are multi-layered, low-opacity, and paired with 1px hairline borders.
- [ ] **Physical Lighting:** Elevated dark cards and dark primary buttons have subtle top-edge light catches instead of flat fills.
- [ ] **Grid Discipline:** All gaps, paddings, and heights are strict multiples of 4px.
- [ ] **Concentric Geometry:** Every nested element's border radius is mathematically smaller than its parent's (`R_inner = R_outer - P`).
- [ ] **Optical Alignment:** Icons, labels, inputs, and buttons share clean alignment rails and matching control heights.
- [ ] **Restrained Display Weight:** Large hero metrics use calm scale (300–500 weight) and tightened letter-spacing (`-0.03em`) instead of heavy bold.
- [ ] **Tabular Figures:** All prices, counts, percentages, and chart numbers use `font-variant-numeric: tabular-nums`.
- [ ] **Zero UI Emojis:** No emojis or excessive exclamation marks in headings, badges, or buttons.
- [ ] **Quiet Metadata:** Secondary counts, dates, and deltas are clean muted text, not loud colorful pill badges.
- [ ] **Uniform Icons:** All icons come from a single vector family with identical stroke width and balanced opacity.
- [ ] **Intentional Negative Space:** Every card and viewport section keeps generous internal breathing room.

## References

- `references/color-and-surfaces.md` , 90/8/2 color ratio, neutral tinting, surface luminance ladder, text contrast tiers, semantic restraint, shadow construction, specular rim lighting, gradient restraint.
- `references/spacing-and-layout.md` , 4px/8px spacing scale, proximity rule, concentric border-radius math, layout proportions (sidebar, nav rows, control heights, button padding, icon rails, line length).
- `references/typography.md` , font pairing archetypes, optical tracking and leading table, tonal compound typography, numeric craft.
- `references/components-and-icons.md` , navigation active states, cards and bento grids, segmented controls, data visualization, iconography rules, microcopy, embedded media.
