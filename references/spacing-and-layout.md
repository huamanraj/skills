# Spatial Architecture, Proportions & Optical Math

Read during Stage 2 (spatial skeleton) and Stage 4 (concentric radii) of the pipeline in SKILL.md.

Great UI looks "effortless" because its geometry obeys strict mathematical relationships. When spacing is arbitrary, the human eye registers subconscious tension.

## 1. Strict spacing scale (the 4px / 8px grid)

All margins, paddings, and gaps MUST be drawn from a single geometric scale. Never invent arbitrary values like `13px`, `19px`, `26px`, or `38px`.

| Token | Value | Primary Use Case |
| :--- | :--- | :--- |
| `space-1` | `4px` | Micro-gaps (label-to-sublabel, icon-to-badge) |
| `space-2` | `8px` | Tight related elements (icon-to-text, button-to-button in a group) |
| `space-3` | `12px` | Compact container padding, list row gaps, nav item internal spacing |
| `space-4` | `16px` | Standard card grid gap, compact card padding, sidebar horizontal padding |
| `space-5` | `20px` | Medium card padding, section-header bottom margin |
| `space-6` | `24px` | Spacious card padding, major section gaps |
| `space-8` | `32px` | Macro page gutters, distinct content block separation |
| `space-12` | `48px` | Hero breathing room, page-level top/bottom anchors |

## 2. The proximity rule (inner vs. outer spacing)

To establish clear visual grouping without cluttering the screen with divider lines, enforce:

- Spacing between groups ≥ 1.5 × spacing within a group.
- Container padding ≥ gap between children.

Example: if cards in a dashboard grid have a 16px gap, internal card padding should be 20–24px, and the spacing between a card's title and its KPI metric should be 8–12px.

## 3. Concentric border radius math

When nesting a rounded element (button, nested task row, active pill, thumbnail) inside a rounded parent card, never give both the exact same radius. Mismatched corners create ugly thick wedges at the diagonals.

Calculate inner radius concentrically:

`R_inner = max(4px, R_outer - P_padding)`

Practical ladder:
- **Outer app shell / floating window:** 20–24px
- **Primary bento card:** 14–16px (with 16–20px padding)
- **Nested row / sub-card / input:** 8–10px
- **Small control / tag / checkbox:** 4–6px
- **Segmented pills & primary pill CTAs:** 9999px (`rounded-full`) — only when height ≤ 44px. Never use `rounded-full` on tall rectangular cards.

## 4. Height, width & layout proportions

Proportional discipline prevents cramped or awkwardly stretched interfaces:
- **Sidebar width:** 220–260px on desktop (240px is the sweet spot). Never let a navigation sidebar exceed 22% of the desktop viewport width.
- **Navigation row height:** 34–40px (36px ideal) with 10–12px horizontal padding and an 8–10px gap between icon and label.
- **Button & input height parity:** standard inputs, search bars, and buttons on the same horizontal axis MUST share identical heights:
  - Compact/dense UI: 32px
  - Standard SaaS/web UI: 36px or 40px
  - Spacious/consumer UI: 44px
- **Button aspect ratio & padding:** horizontal padding ≈ 2 × vertical padding (e.g., `8px 16px` or `10px 20px`) so buttons look balanced rather than boxy.
- **Icon rail alignment:** every icon in a vertical navigation stack shares the exact same left coordinate (x-axis rail) and container box (16px or 18px), even if one section has sub-items or headers. Align section headings to the exact same left rail as the icons below them.
- **Line length (measure):** keep readable prose and card descriptions between 45 and 72 characters per line (`max-width: 60ch`).
