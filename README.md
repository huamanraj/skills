# minimal-ui-craft

An AI agent skill for building minimal, designer-crafted user interfaces — and eliminating generic "AI slop" styling from generated UI.

Works with Claude Code, Cursor, and any agent that supports the [Agent Skills](https://agentskills.io) format. Installable via [skills.sh](https://www.skills.sh).

## What it does

Gives your AI coding agent a complete, theme-agnostic design specification for high-craft minimal UI:

- **Anti-slop diagnostic matrix** — spot and fix saturated gradients, muddy shadows, emoji clutter, loud badges, and other AI-generation tells.
- **Color & surface system** — the 90/8/2 surface ratio, neutral micro-tinting, 4-tier luminance ladders, text contrast tiers, semantic color restraint.
- **Depth & lighting physics** — hairline borders + multi-layer whisper shadows, specular top-edge rim lighting for dark surfaces and primary buttons.
- **Spatial math** — strict 4px/8px grid, proximity rule, concentric border-radius formula, layout proportions.
- **Typography system** — font pairing archetypes, optical tracking/leading table, tonal compound typography, mandatory `tabular-nums`.
- **12-point anti-slop checklist** — a mandatory self-audit before any UI ships.

The skill adapts to any brand color, light or dark mode, and any framework (React, Tailwind, plain CSS). It never hardcodes a single style.

## Install

```bash
npx skills add huamanraj/minimal-ui-craft
```

Or find it from your agent with [find-skills](https://www.skills.sh/vercel-labs/skills/find-skills): search for "minimal ui", "ui design", or "anti-slop".

## Structure

```
minimal-ui-craft/
├── SKILL.md                            # Triggering, core philosophy, 5-stage pipeline, checklist
└── references/
    ├── color-and-surfaces.md           # Color ratio, luminance ladder, shadows, rim lighting
    ├── spacing-and-layout.md           # 4px/8px grid, proximity rule, radius math, proportions
    ├── typography.md                   # Font pairings, tracking/leading, tabular numbers
    └── components-and-icons.md         # Nav, cards, charts, icons, microcopy
```

## When it triggers

Ask your agent to design, build, review, or restyle any web UI — dashboards, landing pages, SaaS apps, admin panels, settings screens — and it applies the spec. Especially useful when output looks generic or "AI-generated."

## License

MIT
