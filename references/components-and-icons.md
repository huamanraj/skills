# Component Craft, Iconography & Microcopy

Read during Stage 5 (polish pass) of the pipeline in SKILL.md, and whenever building navigation, cards, segmented controls, charts, or icon systems.

## 1. Navigation & active states

- **Keep inactive items quiet:** `text-secondary` with transparent backgrounds.
- **Make active items tactile, not loud:** instead of flooding an active sidebar link with a bright saturated brand rectangle:
  - Light mode: elevated crisp white pill/card on a tinted sidebar, hairline border, whisper shadow, and `text-primary` (font-weight 500).
  - Dark mode: slightly raised neutral surface (+4% luminance) with a subtle 1px top specular edge and crisp `text-primary`.
- **De-clutter counters:** replace bright glowing pill badges next to nav items (`18`, `64`, `210`) with quiet, right-aligned `tabular-nums` in `text-tertiary`. Reserve a solid high-contrast dot or pill strictly for genuinely urgent unread alerts.

## 2. Cards & bento grids

- **Header anatomy:** top-left subtle title (13–14px, `text-secondary` or `text-primary`), optional top-right quiet action (`ALL`, `→`, or compact segmented control `DAY / WK / MO`). Never add thick horizontal divider lines under card headers unless the card contains a scrollable table.
- **Breathing room:** at least 25–35% of a minimal card's interior stays clean negative space. Do not pack four unrelated charts, three paragraphs, and two buttons into one card.
- **Nested rows:** inside list cards (to-do lists, alert feeds, chat histories), separate items using either delicate concentric sub-cards (1px ultra-low-opacity border) OR subtle 1px inset hairline dividers — never both heavy boxes and heavy shadows at once.

## 3. Segmented controls & micro-interactions

- Group mode switches (`Day / Week / Month`) inside a recessed pill track (`surface-canvas` or `rgba(0,0,0,0.04)`) with 2–3px internal padding.
- Elevate the active segment with `surface-raised`, a crisp 1px shadow, and concentric inner pill radius.

## 4. Data visualization craft

- **Gridlines:** horizontal hairlines only, at 4–6% foreground opacity. Remove vertical gridlines unless strictly required for dense time-series data.
- **Bars & splines:** avoid thick neon bars with heavy blur glows. Use thin, crisp strokes (1.5–2px) for line/area charts, understated muted fills with subtle vertical fade-to-transparent gradients, and delicate tick-marks or slender columns for bar charts.
- **Axes:** axis labels in 10–11px `text-tertiary` with `tabular-nums`. Remove redundant axis spines when horizontal gridlines already anchor the eye.

## 5. Strict iconography rules

- **Zero emojis in UI chrome:** never use system emojis as interface icons, button decorations, or status markers. They destroy visual consistency and instantly signal AI-generated templates.
- **Single family & uniform stroke:** one cohesive vector icon set (Lucide, Phosphor, Tabler, Heroicons) with consistent stroke width (1.5px for 16–20px icons; 1.75px for 24px icons).
- **Icon-to-text sizing:** pair 14px text with 16px icons; pair 13px text with 15–16px icons. Icons sit at 70–85% of the adjacent text's luminance unless active, so icons never overpower labels.

## 6. Calm, objective microcopy

- Replace hype-driven filler (`"Welcome back, User!"`, `"+12%!!"`, `"Unleash your workflow!"`) with crisp, high-signal language (`"Overview"`, `"October 2026"`, `"+12% vs last month"`, `"All systems normal"`).
- Omit unnecessary exclamation marks in dashboards, metrics, and utility software.

## 7. Cohesive embedded media

- Embedded illustrations, credit cards, avatars, or thumbnails must harmonize with the surface polarity. In dark minimal UIs use matte dark-toned assets rather than bright clipart; in light minimal UIs softly round image corners concentrically and frame them with a 1px inner border (`inset 0 0 0 1px rgba(0,0,0,0.06)`) so bright photos never bleed into white backgrounds.
