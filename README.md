# minimal-ui-craft

An AI agent skill for building coherent, accessible, responsive user interfaces and eliminating generic "AI slop" styling from generated UI.

Works with Claude Code, Cursor, and any agent that supports the [Agent Skills](https://agentskills.io) format. Installable via [skills.sh](https://www.skills.sh).

## What it does

Gives your AI coding agent a complete, theme-agnostic design specification for high-craft minimal UI, from page composition down to pixels:

- **Anti-slop diagnostic matrix:** spot and fix saturated gradients, muddy shadows, emoji clutter, loud badges, repetitive card grids, and other AI-generation tells.
- **Product adaptation:** classify the interface (SaaS, landing page, e-commerce, mobile, editorial, developer tool) and adapt priorities before choosing tokens.
- **Color & surface system:** the 90/8/2 neutral ratio as a tunable default, neutral micro-tinting, 4-tier luminance ladders, text contrast tiers, semantic color restraint.
- **Depth & lighting physics:** hairline borders, multi-layer whisper shadows, specular top-edge rim lighting for dark surfaces and primary buttons.
- **Spatial math:** 4px/8px base grid with optical judgment, proximity rule, concentric border-radius rule of thumb, layout proportions.
- **Typography system:** font pairing archetypes, optical tracking/leading starting points, tonal compound typography, `tabular-nums`.
- **Page composition:** focal points, asymmetry, intentional whitespace, card restraint, visual storytelling at the page level.
- **Responsive layout:** breakpoints, fluid typography, grid collapse rules, adaptive density, overflow audits.
- **Interaction & motion:** full state sets (hover, focus, pressed, loading, disabled, empty, error, success), async feedback, transition timing and easing, reduced motion.
- **Accessibility:** WCAG contrast, keyboard navigation, focus visibility, touch targets, screen reader support.
- **Media & content craft:** photography selection and crops, image-to-text balance, realistic content, truncation, empty states, complete component patterns and edge cases.
- **Visual QA protocol:** a mandatory render-inspect-refine loop with real screenshots at 375px, 768px, and 1440px, fixing the biggest defects first.
- **17-point quality checklist:** a mandatory self-audit before any UI ships.

The goal is not to make every component look polished in isolation; it is to make the whole product feel coherent, intentional, and easy to use. The skill adapts to any brand color, light or dark mode, and any framework (React, Tailwind, plain CSS). It never hardcodes a single style.

## Install

```bash
npx skills add huamanraj/skills --skill minimal-ui-craft
```

Or find it from your agent with [find-skills](https://www.skills.sh/vercel-labs/skills/find-skills): search for "minimal ui", "ui design", or "anti-slop".

## Structure

```
minimal-ui-craft/
├── SKILL.md                            # Triggering, core philosophy, 8-stage pipeline, checklist
└── references/
    ├── product-adaptation.md           # Product-type classification, per-type design priorities
    ├── color-and-surfaces.md           # Color ratio, luminance ladder, shadows, rim lighting
    ├── spacing-and-layout.md           # Base grid, proximity rule, radius math, proportions
    ├── typography.md                   # Font pairings, tracking/leading, tabular numbers
    ├── page-composition.md             # Page-level hierarchy, focal points, card restraint
    ├── responsive-layout.md            # Breakpoints, fluid type, grid collapse, overflow audits
    ├── content-and-components.md       # Realistic content, empty states, component edge cases
    ├── media-and-imagery.md            # Photography selection, crops, image-to-text balance
    ├── interaction-and-motion.md       # State sets, async feedback, timing, reduced motion
    ├── accessibility.md                # Contrast, keyboard, focus, touch targets, screen readers
    ├── components-and-icons.md         # Nav, cards, charts, icons, microcopy
    └── visual-qa.md                    # Render-inspect-refine protocol, browser precision
```

## When it triggers

Ask your agent to design, build, review, or restyle any web UI, including dashboards, landing pages, SaaS apps, admin panels, and settings screens, and it will apply the spec. This is especially useful when output looks generic or "AI-generated."

## License

MIT
