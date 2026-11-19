# Typographic Hierarchy, Font Pairing & Micro-Typography

Read during Stage 3 (typographic hierarchy) of the pipeline in SKILL.md.

In minimal UI, typography is the primary visual texture. A design with ordinary colors and extraordinary typography always outperforms one with trendy colors and sloppy typography.

## 1. Intentional font pairing archetypes

Select a pairing that matches the product's brand personality (or respect the user's provided fonts):

1. **Modern Precision (single neo-grotesque family)**
   - Use for: developer tools, AI workspaces, high-density SaaS, smart-home dashboards.
   - Approach: one crisp sans-serif (`Inter`, `Geist`, `Plus Jakarta Sans`, `SF Pro`, `Satoshi`). Rely on weight contrast (400 vs 500 vs 600), scale jumps, and letter-spacing to create rhythm.
2. **Editorial Warmth (refined serif + clean sans)**
   - Use for: wellness, finance, publishing, calm productivity, boutique B2B.
   - Approach: a calm, legible serif (`Instrument Serif`, `Newsreader`, `Fraunces`, `Lora`, `Georgia`) for page headings, section titles, and hero KPI figures, paired with a neutral sans-serif (`Inter`, `DM Sans`) for navigation, labels, inputs, and body copy. Never use serif fonts for tiny 11px uppercase labels or dense table cells.
3. **Technical / Analytical (clean sans + monospace)**
   - Use for: analytics, telemetry, financial ledgers, infrastructure tools.
   - Approach: neutral sans-serif for interface chrome; crisp monospace (`JetBrains Mono`, `Geist Mono`, `IBM Plex Mono`) for IDs, shortcuts (⌘K), timestamps, API keys, and tabular metrics.

## 2. Optical tracking (letter-spacing) & leading (line-height)

Default browser typography looks amateurish at extreme sizes. Apply inverse scaling: as font size increases, tighten both tracking and line-height.

| Role | Typical Size | Font Weight | Line Height | Letter Spacing |
| :--- | :--- | :--- | :--- | :--- |
| **Hero / Display KPI** | 32–48px | 300, 400, or 500* | 1.05–1.15 | -0.03em to -0.04em |
| **Page Title (H1)** | 22–28px | 500 or 600 | 1.20–1.25 | -0.02em to -0.025em |
| **Card / Section Title** | 14–16px | 500 | 1.30–1.40 | -0.01em |
| **Body / Nav Item** | 13–14px | 400 or 500 | 1.45–1.55 | 0em |
| **Caption / Subtext** | 12–13px | 400 | 1.40–1.50 | 0em |
| **Micro-Label / Axis** | 10–11px | 500 | 1.20 | +0.02em to +0.06em (if uppercase) |

\*Craft secret: avoid heavy 700–800 extra-bold weights on large KPI numbers (`$48,210`, `64°`, `€ 6,245.01`). Large display figures look dramatically more refined at 300 (Light), 400 (Regular), or 500 (Medium) — let scale do the work instead of heavy ink density.

## 3. Tonal compound typography

Instead of breaking related context into cluttered separate boxes, split a single phrase using luminance contrast:
- Date header: `October` (text-primary) + `2026` (text-tertiary)
- Metric + unit: `840` (32px, text-primary) + `kWh` (11px, text-tertiary, baseline-aligned)
- Delta metric: `+12%` (semantic-positive) + `vs last month` (text-tertiary)

## 4. Mandatory numeric craft

For every metric, price, counter, clock, chart axis, and table column:

```css
font-variant-numeric: tabular-nums;
```

Tabular figures give every digit identical horizontal width so numbers align cleanly in columns and never jitter when values update.
