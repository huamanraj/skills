---
name: minimal-ui-craft
description: Build minimal, designer-crafted user interfaces and eliminate generic "AI slop" styling. Use this skill whenever designing, building, reviewing, or restyling any web UI, including dashboards, landing pages, SaaS apps, admin panels, settings screens, or individual components. It is especially useful when the user asks for a minimal, clean, premium, or designer-quality look, mentions "AI slop", or says generated UI looks generic or amateurish. Covers page composition, responsive layout, interaction states, accessibility, motion, imagery, realistic content, and a mandatory visual QA pass. The rules are theme-agnostic and adapt to any brand color, light or dark mode, and any framework (React, Tailwind, plain CSS, etc.).
---

# Minimal UI Craft

A universal, theme-agnostic UI engineering and visual design specification: the structural, optical, typographic, and lighting rules that separate designer-crafted minimalism from generic "AI slop." Apply these principles dynamically on top of any user-provided design system, brand palette, or layout spec; never hardcode a single style or color scheme.

The goal is not to make every component look polished. The goal is to make the whole product feel coherent, intentional, and easy to use. Agents routinely produce interfaces with individually beautiful cards that still read as generic AI output; the fix lives at the page level as much as the component level.

## Core philosophy

Minimalism is not the absence of styling; it is the deliberate removal of visual friction so that proportion, typography, surface contrast, and light carry the entire hierarchy.

"AI slop" fails because it compensates for weak hierarchy with louder styling: heavy glows, saturated backgrounds, chunky drop shadows, rainbow badges, oversized radii, and emoji clutter. High-craft minimal UI achieves clarity through restraint, tonal stepping, and optical precision.

Good design requires judgment, not blind application of fixed numbers. Every quantitative rule in this skill is a well-calibrated default: follow it unless the rendered result argues otherwise, and always judge the rendered result.

## Diagnostic matrix: slop vs. craft

| Visual Dimension | Generic "AI Slop" (Anti-Pattern) | Designer-Crafted Minimalism (Target) |
| :--- | :--- | :--- |
| **Page Composition** | Every section is the same card grid; equal visual weight everywhere; content forced into templates. | One dominant focal point per section; mixed layout devices (open space, lists, images, cards); layout shaped by the actual content. |
| **Color Usage** | Saturated gradients across backgrounds, cards, and borders simultaneously; brand color plastered on 40%+ of pixels. | Neutral-first foundation. Brand color reserved for primary actions, active signals, and focal accents. |
| **Depth & Elevation** | Single heavy, muddy black shadow (`0 10px 25px rgba(0,0,0,0.4)`) or completely flat elements with zero separation. | Separation matched to hierarchy: subtle surface-luminance steps, hairline borders, multi-layer ambient shadows, directional top-edge highlights. A surface may use a border, a shadow, both, or neither. |
| **Spacing & Rhythm** | Arbitrary vertical gaps (`13px`, `26px`, `44px`, `30px`) and misaligned container rails. | A disciplined base spatial grid (4px / 8px) with deliberate optical exceptions, proximity grouping, and razor-sharp alignment rails. |
| **Typography** | Heavy bold weights everywhere, identical luminance for labels and values, default letter-spacing on large headings, non-tabular numbers. | Tonal hierarchy (weight + opacity + scale), display tracking tuned to the rendered face, crisp pairings, and `tabular-nums` for numeric data. |
| **Border Radius** | Identical large radius slapped onto both parent containers and tightly nested children, causing awkward corner pinching. | Concentric radii (`R_inner = R_outer - Padding`) for genuinely nested shapes, scaled proportionally to element height. |
| **Badges & Counters** | Bright, glowing pill backgrounds around every status, tag, and numeric count. | Plain right-aligned muted numerals for counts; low-opacity tinted pills or `6px` status dots for semantic states. |
| **Iconography & Copy** | Emojis as default UI icons, exclamation marks (`+12%!!`), mixed icon libraries, inconsistent stroke weights. | Monochrome vector icons with uniform stroke weight (`1.5px` or `1.75px`), calm objective microcopy. |
| **States & Motion** | Only the default state exists; hover is an afterthought; instant or bouncy transitions. | Every interactive element ships hover, focus, pressed, disabled, and loading states; motion is short, quiet, and respects reduced-motion. |
| **Responsiveness** | A desktop layout squeezed into mobile; horizontal overflow; untested breakpoints. | Layout, density, and typography adapt per breakpoint; verified at 375px, 768px, and 1440px with zero unintended overflow. |
| **Data Visualization** | Thick glowing bars, neon fills, loud legends, and cluttered gridlines. | Fine strokes, restrained opacity gradients, subtle axis hairlines, and crisp direct-read metrics. |

## Execution pipeline

Run this pipeline before writing final UI code. Each stage has a reference file with the full rules. Read it when you reach that stage.

### Stage 0: Identify the product and its experience priorities
Classify the interface (SaaS dashboard, marketing landing page, e-commerce, mobile app, editorial site, developer tool) and decide what that type demands: density, imagery, type scale, motion budget, and reading pattern. A landing page and a dashboard should never get the same layout instincts.
→ Full rules: `references/product-adaptation.md`

### Stage 1: Ingest brand and derive tokens
Read the user's polarity (light, dark, or both), primary brand color, typography preference, and information density. Derive the 4-tier neutral surface ramp, 4-tier text contrast ramp, hairline border opacity, and 2-layer elevation shadows as CSS custom properties (`--surface-0` to `--surface-3`, `--text-1` to `--text-4`, `--border-subtle`, `--radius-card`, `--radius-inner`).
→ Full rules: `references/color-and-surfaces.md`

### Stage 2: Establish spatial skeleton
Lock the layout grid (4px/8px spacing scale by default), sidebar width, and max content width. Verify every vertical alignment rail (sidebar logo, search input, nav headers, nav icons, page title, content left edge) aligns to exact grid coordinates.
→ Full rules: `references/spacing-and-layout.md`

### Stage 3: Construct typographic hierarchy
Assign font families or weights per the pairing archetype that fits the product. Tune display tracking to the rendered face, apply `tabular-nums` to all numeric figures, and set tonal contrast for compound titles and metric-unit pairs.
→ Full rules: `references/typography.md`

### Stage 4: Craft surfaces and micro-depth
Establish separation with surface luminance stepping first; add hairline borders, feathered multi-layer shadows, both, or neither according to each surface's hierarchy. Apply specular top-edge highlights on elevated dark surfaces and dark primary buttons. Verify concentric radii on genuinely nested elements.
→ Full rules: `references/color-and-surfaces.md` (depth & lighting), `references/spacing-and-layout.md` (radius math)

### Stage 5: Compose pages with real content
Design at the page level: one focal point per section, mixed layout devices instead of repeated card grids, and layouts shaped by real copy and realistic data. Make the layout responsive across mobile, tablet, and desktop, and art-direct any imagery.
→ Full rules: `references/page-composition.md`, `references/responsive-layout.md`, `references/content-and-components.md`, `references/media-and-imagery.md`

### Stage 6: Wire interaction states, motion, and accessibility
Every interactive element gets its full state set (hover, focus, pressed, disabled, loading). Forms, tables, dialogs, tooltips, and notifications get their edge cases. Motion is quiet and respects reduced-motion. Contrast, keyboard navigation, focus visibility, and touch targets are verified, not assumed.
→ Full rules: `references/interaction-and-motion.md`, `references/accessibility.md`, `references/components-and-icons.md`

### Stage 7: Render, inspect, refine (mandatory visual QA)
Never trust generated CSS on faith. Render the interface in a real browser when one is available, capture screenshots at 375px, 768px, and 1440px, and fix the biggest visible problems before polishing details. Then run the anti-slop checklist below.
→ Full protocol: `references/visual-qa.md`

## The anti-slop checklist

Verify every checkpoint before considering a minimal UI complete. Each quantitative bar is a default, not a dogma; deviations must be deliberate and verified visually.

- [ ] **Calm Foundation:** For neutral SaaS-style interfaces, at least 85–90% of the viewport is calm neutral surfaces. Marketing and editorial products may carry more color, but accents stay reserved for actions and focal points.
- [ ] **No Muddy Shadows:** Drop shadows are multi-layered and low-opacity. Each elevated surface uses a border, a shadow, both, or neither, chosen by its hierarchy.
- [ ] **Physical Lighting:** Elevated dark cards and dark primary buttons have subtle top-edge light catches instead of flat fills.
- [ ] **Grid Discipline:** Gaps, paddings, and heights follow the 4px scale by default; exceptions are deliberate optical adjustments, not arbitrary numbers.
- [ ] **Concentric Geometry:** Genuinely nested rounded elements use mathematically smaller radii than their parents (`R_inner = R_outer - P`).
- [ ] **Optical Alignment:** Icons, labels, inputs, and buttons share clean alignment rails and matching control heights.
- [ ] **Restrained Display Weight:** Large hero metrics use calm scale (300–500 weight) and letter-spacing tuned to the rendered font instead of heavy bold.
- [ ] **Tabular Figures:** All prices, counts, percentages, and chart numbers use `font-variant-numeric: tabular-nums`.
- [ ] **No Default Emoji Icons:** No emojis as interface icons, badges, or button decorations, unless the product or content genuinely calls for them.
- [ ] **Quiet Metadata:** Secondary counts, dates, and deltas are clean muted text, not loud colorful pill badges.
- [ ] **Uniform Icons:** All icons come from a single vector family with identical stroke width and balanced opacity.
- [ ] **Purposeful Density:** Card and section density matches purpose; marketing surfaces breathe, data-dense surfaces stay compact.
- [ ] **Page-Level Hierarchy:** Every section has one dominant focal point, and no two adjacent sections repeat the same card grid.
- [ ] **Responsive Integrity:** Layout verified at 375px, 768px, and 1440px with zero unintended horizontal overflow and adapted density.
- [ ] **Complete States:** Hover, focus, pressed, loading, disabled, empty, error, and success states exist and were exercised, not just the default screen.
- [ ] **Accessible by Default:** Contrast meets WCAG targets, keyboard navigation works with a visible focus indicator, and touch targets are large enough.
- [ ] **Visually Verified:** The interface was rendered and inspected in a real browser, and the most noticeable problems were fixed before shipping.

## References

- `references/product-adaptation.md`: product-type classification and per-type design priorities (Stage 0).
- `references/color-and-surfaces.md`: color ratio discipline, neutral tinting, surface luminance ladder, text contrast tiers, semantic restraint, shadow construction, specular rim lighting, gradient restraint (Stages 1, 4).
- `references/spacing-and-layout.md`: 4px/8px spacing scale, proximity rule, concentric border-radius math, layout proportions (Stages 2, 4).
- `references/typography.md`: font pairing archetypes, optical tracking and leading table, tonal compound typography, numeric craft (Stage 3).
- `references/page-composition.md`: page-level hierarchy, focal points, asymmetry, card restraint, visual storytelling (Stage 5).
- `references/responsive-layout.md`: breakpoints, fluid typography, grid collapse rules, adaptive density, overflow audits (Stage 5).
- `references/content-and-components.md`: realistic content, truncation and long-text behavior, empty states, and complete component patterns (forms, tables, dialogs, tooltips, notifications, skeletons) (Stage 5).
- `references/media-and-imagery.md`: photography selection, crops, object positioning, image-to-text balance, responsive image performance (Stage 5).
- `references/interaction-and-motion.md`: full interaction state sets, async feedback, transition timing and easing, hover movement, reduced motion, layout-shift prevention (Stage 6).
- `references/accessibility.md`: WCAG contrast, keyboard navigation, focus visibility, touch targets, screen reader support (Stage 6).
- `references/components-and-icons.md`: navigation active states, cards, segmented controls, data visualization, iconography rules, microcopy, embedded media (Stage 6).
- `references/visual-qa.md`: the render-inspect-refine protocol, screenshot widths, device-pixel rendering, font loading, layout stability, browser testing (Stage 7).
