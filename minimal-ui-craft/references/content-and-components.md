# Content-First Layout & Component Completeness

Read during Stage 5 (page composition) of the pipeline in SKILL.md.

Interfaces are designed with real content, not placeholders. A layout that only works with "Lorem ipsum" and two-word names is a fiction that breaks on contact with users.

## 1. Design with realistic content

- Use plausible real data from the start: full names (including long ones), realistic prices, uneven list lengths, actual dates. "John Doe" and "Test 123" hide every wrapping and overflow problem.
- Design for the extremes, not the average: the longest reasonable name, the empty list, the 10,000-row table, the headline that wraps to three lines, the metric that is temporarily missing.
- Headline wrapping is designed, not accidental: set `max-width` on display copy, check the break points at each viewport width, and use `text-wrap: balance` on headings so wraps fall gracefully.

## 2. Truncation and long-text behavior

- Truncate single-line values with ellipsis (`text-overflow: ellipsis`), never mid-word breaks, and always offer the full value on hover/focus (title attribute or tooltip).
- Multi-line clamping (`-webkit-line-clamp`) for previews and card excerpts; pick a line count that preserves the grid's rhythm.
- IDs, URLs, hashes, and emails get `overflow-wrap: anywhere` or monospace-plus-truncation treatment (truncate the middle when both ends identify the value, for example `0c1f...977c`).
- Never truncate what the user came to read: article bodies, messages, and primary content expand or scroll; only metadata and previews clamp.

## 3. Content density by volume

Density follows the actual data: a dashboard with three metrics breathes; one with thirty rows tightens. Do not stretch sparse content to fill a fixed template (giant cards with two words in them) or cram rich content into a sparse one.

## 4. Component patterns and edge cases

Every component below is incomplete until its edge cases are designed.

### Forms
- Inline validation on blur or submit (never per-keystroke nagging), messages adjacent to the field, error summary with `role="alert"` on submit failure.
- Submit button disabled or clearly gated until the form is submittable; loading state on submit; input preserved after errors.
- Labels always visible (placeholders are hints, not labels); required fields marked; help text in quiet metadata styling.

### Tables
- Sortable columns indicate state (arrow on the active column); header can stick on vertical scroll.
- Row hover highlight (2-4% luminance); zebra striping only if rows are hard to track.
- Numeric columns right-aligned with `tabular-nums`; primary identifier column left-aligned.
- Designed empty state ("No invoices yet" plus the one action that creates the first), designed loading state (skeleton rows), and a mobile strategy (horizontal scroll in a contained region or stacked cards; see `responsive-layout.md`).

### Dropdowns and selects
- Keyboard operable (arrows, Enter, Escape), focus returns to the trigger on close.
- Menu elevation follows the overlay surface tier with the floating shadow reserved for it (see `color-and-surfaces.md`).

### Dialogs and modals
- Focus trapped inside, opens from and returns to the invoking control, closes on Escape and on backdrop click (unless destructive mid-flow).
- Title names the action; the primary button repeats it ("Delete project", never bare "OK").

### Tooltips
- Short delay (~300-500ms) on hover, instant on keyboard focus, dismissed by Escape.
- Never the only carrier of essential information; they annotate, they do not substitute for labels.

### Notifications and toasts
- Fixed position (top-right or bottom-center), stacked newest-last, auto-dismiss after ~5 seconds unless they require action, always manually dismissible, announced to screen readers (`role="status"`).
- One at a time in spirit: a burst of events collapses into a summary, not a tower of banners.

### Skeletons and async regions
- Skeleton blocks mirror the final layout's geometry (same heights, same rails) in a low-contrast shimmer; reserved for loads over ~300ms.
- Error state for every async region: a quiet message plus a retry action, never an infinite spinner.

## 5. The universal edge-case list

For every screen, answer all five before shipping: **loading** (what shows while data arrives), **empty** (what shows with zero items), **error** (what shows when the request fails), **partial** (what shows when some data is missing), and **overflow** (what happens with far more content than designed for).
