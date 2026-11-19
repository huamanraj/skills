# Page Composition & Visual Storytelling

Read during Stage 5 (page composition) of the pipeline in SKILL.md.

This file covers the most common failure of AI-generated UI: individually polished components arranged into a page that still looks generic. Styling a card beautifully is not the same as knowing when a card should exist at all.

## 1. Not every piece of content needs a card

AI agents default to boxing everything: Feature A in a card, Feature B in an identical card, Feature C in a third. Even with perfect shadows and radii, the result is a repetitive grid where everything has equal visual importance and nothing leads the eye.

Compose pages from mixed layout devices instead:

- **Open layouts:** bare sections separated by whitespace alone. Often the strongest choice; try it first.
- **Bordered sections:** a hairline top or bottom rule to divide major bands without boxing content.
- **Compact lists:** rows with hairline dividers for homogeneous, scannable items.
- **Images and media blocks:** full-bleed or inset, used as structural elements, not decoration.
- **Cards:** reserve for genuinely independent, self-contained units (a metric tile, a pricing tier, a product) or for content that must feel lifted out of the page flow.

If every section uses the same device, the page is under-composed. If a section works with the decoration removed, remove it.

## 2. One dominant focal point per section

Every viewport-height section needs a single element that wins attention first: a headline, a hero metric, a product shot, a primary CTA. Supporting elements step down deliberately.

- Establish the focal point through scale, contrast, or position, never through louder decoration.
- Demote everything else: secondary actions become quiet text links, supporting metrics shrink, ornament recedes.
- If two elements compete at equal weight, pick one and demote the other. Ambiguous hierarchy reads as noise.

## 3. Asymmetry with intent

Perfectly mirrored, centered layouts are safe and forgettable. Asymmetry creates hierarchy and movement:

- Offset a headline left with supporting media or a stat block right (60/40 or 70/30 splits).
- Stagger feature blocks vertically instead of a flat 3-across row.
- Break the grid on purpose for the focal element, then return to the grid for everything else. Contrast only reads as intentional when order surrounds it.

## 4. Align layout to actual content

Never force content into a template. Two features are not a three-column grid; a long feature list is not a hero. Count and weigh the real content first, then choose the composition:

- 1 item: full-width spotlight, generous whitespace.
- 2 items: asymmetric split, primary and secondary weight.
- 3-4 items: grid acceptable, vary span or emphasis to avoid monotony.
- 5+ items: compact list or table, not cards.

## 5. Visual storytelling for landing pages

Dashboards tolerate repetition; landing pages die from it. A marketing page is a narrative sequence, not a stack of bento grids:

1. **Hook:** one sharp headline and one primary action. Nothing else competes.
2. **Proof:** product shown in context (real UI, real data), not abstract illustration.
3. **Substantiation:** features framed as outcomes, varied composition per block.
4. **Trust:** logos, numbers, or quotes in quiet, compact treatments.
5. **Close:** a single repeated call to action with the same wording as the hook.

Vary the layout device between adjacent sections: open text, then media, then a list, then a single card. Never repeat the same bento grid down the page.

## 6. The decoration removal test

When a composition feels off, remove instead of adding: drop the card wrapper, the border, the shadow, the badge, the divider. If the section improves, the decoration was compensating for weak hierarchy. Fix the hierarchy (scale, spacing, weight) rather than re-adding ornament.
