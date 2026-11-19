# Responsive Layout & Adaptive Density

Read during Stage 5 (page composition) of the pipeline in SKILL.md.

A design that only works at 1440px is not finished. Layout, typography, and density must adapt across mobile, tablet, and desktop, and the result must be verified at real widths (see `visual-qa.md`).

## 1. Breakpoint model

Design and verify at three canonical widths, matching the visual QA protocol:

| Class | Width | Layout instincts |
| :--- | :--- | :--- |
| **Mobile** | 375px | Single column. Stacked sections. Sticky bottom actions where useful. Density reduced: hide tertiary metadata, collapse secondary actions into menus. |
| **Tablet** | 768px | Two-column where content allows. Sidebar collapses to icons or a drawer. Cards go 2-across. |
| **Desktop** | 1280-1440px | Full multi-column layout. Sidebar visible. Content capped at a max width (never let prose or dashboards stretch edge to edge on wide screens). |

Use mobile-first CSS: write the single-column layout as the default, then layer on complexity with `min-width` queries. Prefer container queries for components whose layout depends on their own width rather than the viewport's (a card in a sidebar vs. in the main column).

## 2. Fluid typography

Type should scale with the viewport instead of jumping at breakpoints. Use `clamp()` for display and heading sizes:

```css
.hero-title { font-size: clamp(1.75rem, 1.1rem + 3vw, 3rem); }
.page-title { font-size: clamp(1.375rem, 1.2rem + 0.8vw, 1.75rem); }
```

Body text stays stable (13-16px at all widths). Line length still governs: cap prose at 45-72 characters on every breakpoint.

## 3. Grid collapse rules

Multi-column grids must degrade predictably:

- 4 columns (desktop) → 2 columns (tablet) → 1 column (mobile), or 3 → 2 → 1. Never 3 → 1 directly; intermediate widths matter.
- Sidebar layouts: sidebar becomes an overlay drawer or icon rail on tablet, and hides behind a hamburger or bottom nav on mobile. Content never squeezes beside a shrunken sidebar.
- Asymmetric splits (60/40) stack vertically on mobile, focal element first. The element that won attention on desktop leads the stack on mobile.

## 4. Adaptive density

Density is a per-breakpoint decision, not a constant:

- **Hide, do not shrink:** on mobile, drop tertiary metadata, secondary columns, and decorative media rather than shrinking everything into illegibility.
- **Collapse controls:** filter rows become a filter sheet or accordion; multi-button toolbars collapse into an overflow menu.
- **Touch targets:** interactive elements are at least 44x44px on touch layouts, with 8px separation (see `accessibility.md`).
- **Tables:** switch to horizontal scroll within a contained region, or transform rows into stacked cards with the key field as the row title. Never let a table force page-level horizontal scroll.

## 5. Overflow audit

Unintended horizontal overflow is the most common responsive defect. At every verified width:

- `document.documentElement.scrollWidth` must equal `clientWidth`. Any positive difference is a bug to fix, not to mask with `overflow-x: hidden` on the body.
- Common causes: fixed-width elements, long unbroken strings (URLs, IDs), negative-margin tricks, `100vw` on pages with a vertical scrollbar, absolute-positioned decorations. Find the offending element and fix it at the source.
- Long strings get `overflow-wrap: anywhere` or truncation, never page overflow.

## 6. Mobile chrome details

- Respect safe areas: pad fixed bottom bars with `env(safe-area-inset-bottom)`.
- Sticky headers stay slim; do not stack a sticky nav over a sticky subheader over a sticky filter bar.
- Test at the small end too: 320-360px widths must remain usable, not just 375px.
