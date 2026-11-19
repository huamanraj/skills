# Accessibility & Usability

Read during Stage 6 (states, motion, accessibility) of the pipeline in SKILL.md.

Accessibility is not a compliance pass bolted on at the end; it is a set of hard constraints that shape surfaces, contrast, and interaction from the start. A minimal interface that fails these is not minimal, it is broken.

## 1. Contrast (WCAG)

- **Body text:** at least 4.5:1 against its surface.
- **Large text (18px+ or 14px+ bold):** at least 3:1.
- **UI components and graphical objects:** at least 3:1 against adjacent colors (borders of inputs, icon glyphs, focus rings).
- The `text-secondary` and `text-tertiary` tiers in `color-and-surfaces.md` are calibrated to these floors; verify the actual rendered pairs with a contrast checker, especially when tinting neutrals.
- Never place text over imagery without a scrim or backing surface that guarantees the ratio (see `media-and-imagery.md`).
- Never convey meaning by color alone: pair semantic color with an icon, label, or shape (an error row gets an icon and text, not just a red tint).

## 2. Keyboard navigation

- Every interactive element is reachable and operable by keyboard alone: links, buttons, menus, dialogs, tabs, custom controls.
- Tab order follows the visual reading order; no positive `tabindex` values reordering the page.
- Semantic HTML first: `<button>` for actions, `<a>` for navigation, `<input>` with a linked `<label>`, `<nav>`, `<main>`, `<table>` for tabular data. Reach for ARIA only when native semantics cannot express the widget.
- Custom widgets follow their standard pattern: menus use arrow keys and Escape, tabs use arrow keys, dialogs cycle focus internally.
- No keyboard traps anywhere except a modal dialog's intentional focus loop, which must close on Escape.

## 3. Focus visibility

- A visible focus indicator on every interactive element: 2px outline or ring in the accent color, 2px offset, with at least 3:1 contrast against the surface.
- Use `:focus-visible` so pointer users are not shown persistent rings while keyboard users keep them.
- Never ship `outline: none` without an equal or stronger replacement.

## 4. Touch targets

- Minimum 44x44px (Apple HIG) or 48x48px (Material) for every touch target, with at least 8px separation between adjacent targets.
- Small visual glyphs can sit inside larger hit areas: expand with padding, not with visible bulk.
- Destructive actions get extra separation from primary actions.

## 5. Screen reader support

- Every image that carries meaning has descriptive alt text; purely decorative images get empty `alt=""` so they are skipped.
- Icon-only buttons have an accessible name (`aria-label` or visually hidden text). An icon with no name is an empty button to a screen reader.
- Form fields have programmatically associated labels; placeholder text is never the label.
- Status changes that happen without focus (a toast, an async save confirmation, a validation error summary) are announced with a live region (`role="status"` or `aria-live="polite"`; assertive only for genuine emergencies).
- Headings form a real outline: one h1 per page, no skipped levels used for visual sizing.

## 6. Motion and cognitive load

- Respect `prefers-reduced-motion` (see `interaction-and-motion.md`).
- Nothing flashes more than three times per second.
- Auto-playing carousels and marquees are banned in professional interfaces; if content rotates, the user controls it.

## 7. Error prevention and recovery

- Destructive or irreversible actions get a confirmation that names the consequence.
- Error messages say what happened and how to fix it, in plain language, placed next to the problem (`role="alert"` for the summary).
- Preserve user input on errors; never clear a form because one field failed.
