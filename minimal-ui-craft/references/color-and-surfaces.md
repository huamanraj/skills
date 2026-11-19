# Color Architecture, Surfaces, Depth & Lighting

Read during Stage 1 (token derivation) and Stage 4 (surface craft) of the pipeline in SKILL.md.

## 1. Color architecture and tonal discipline

Never judge a color palette in isolation; judge it by proportional area and luminance separation. Regardless of the brand color supplied, enforce the following architecture.

### The 90 / 8 / 2 surface ratio
The neutral-dominant split below is the default for neutral SaaS interfaces and dashboards, not a universal law: editorial, marketing, and playful consumer products can carry more brand color (see `product-adaptation.md`). What stays constant is the discipline behind it: the canvas stays neutral and quiet, and high-chroma color stays reserved for actions and focal points so the hierarchy never shouts.
- **90% Neutral Canvas & Surfaces:** backgrounds, sidebars, cards, dividers, standard text.
- **8% Tinted Neutrals & Secondary Accents:** subtle hover states, active container tints, muted badges, secondary chart series.
- **2% High-Chroma Focal Accent:** primary CTA button, active focus rings, critical alerts, key focal metrics.

### Neutral tinting (preventing "dead gray" and "neon soup")
Pure sterile gray (`#808080`) or pure pitch black (`#000000`) looks harsh or lifeless; heavily saturated backgrounds look amateurish.
- **Warm or cool micro-tinting:** infuse neutral backgrounds with a microscopic amount of the brand hue (chroma ≤ 0.015 in OKLCH, or saturation ≤ 6% in HSL).
 - Cool/editorial light: canvas shifts almost imperceptibly toward cool sage or slate while cards remain crisp white.
 - Warm/ambient light: canvas uses warm alabaster (`#F6F5F2`) paired with pure white or soft cream cards.
 - Refined dark: avoid bright indigo/purple-washed dark modes. Anchor dark surfaces in deep neutral charcoal (luminance ~4%–14%) with ultra-low saturation (≤ 8%).

### Surface luminance ladder
Create figure-ground separation without heavy lines by defining four discrete surface tiers:

1. **`surface-canvas` (Level 0):** deepest base viewport or sidebar wash.
2. **`surface-base` (Level 1):** primary workspace or standard card surface.
3. **`surface-raised` (Level 2):** elevated cards, active segmented controls, dropdowns, popovers.
4. **`surface-overlay` (Level 3):** modals, floating command palettes, sticky tooltips.

- **Light mode:** higher elevation moves slightly brighter (canvas at 96% lightness → card at 100%) paired with a micro-shadow.
- **Dark mode:** higher elevation moves **lighter**, never darker (canvas at 6% → card at 9% → active/popover at 13%). Light behaves physically: surfaces closer to the viewer catch more ambient light.

### Text contrast tiers (luminance hierarchy)
Never use just one text color. Define four semantic levels derived from the foreground polarity:
- **`text-primary`:** high contrast (≥ 12:1 on base surface; avoid raw `#000000` on `#FFFFFF`; use `#0F1115` or `#111111` in light mode, and `#F3F4F6` or `#EDEDEF` in dark mode to reduce halation).
- **`text-secondary`:** supporting copy, subtitles, inactive navigation (~60–70% contrast strength; target ≥ 4.5:1).
- **`text-tertiary`:** metadata, timestamps, axis labels, placeholder text, secondary headline tokens (~40–50% contrast strength).
- **`text-quaternary`:** disabled states and ultra-subtle structural hints.

### Semantic color restraint
When rendering positive/negative deltas, warnings, or statuses:
- Never put full-saturation solid backgrounds behind semantic tags (e.g., avoid bright neon green pills).
- Use low-opacity tinted fills (8–14% opacity of the semantic hue) paired with a high-contrast text shade of the same hue, or render plain text with a single 6px semantic dot or crisp directional arrow (↑ / ↓).

## 2. Surface elevation, depth & lighting physics

The #1 tell of AI-generated minimal UI is either muddy, blurry drop shadows or flat wireframe emptiness. Real minimalism uses subtle optical physics to make surfaces feel physical and tactile.

### Separating surfaces: borders, shadows, or both
A shadow alone can look blurry; a border alone can look flat and boxy. The safest default for an elevated card is a crisp 1px boundary paired with a feathered ambient shadow, but it is not a law: choose a border, a shadow, both, or neither according to the surface's place in the hierarchy. Flat sections inside one continuous surface need no separation at all; a card sitting directly on the canvas often reads cleanly with a hairline border alone; floating overlays earn a real shadow (see the ladder in `page-composition.md`).

```css
/* Light Mode Elevated Surface (Card / Active Pill): border + whisper shadow */
.surface-elevated-light {
  background: var(--surface-raised);
  border: 1px solid rgba(15, 23, 42, 0.06); /* Crisp boundary */
  box-shadow:
    0 1px 2px rgba(15, 23, 42, 0.04),       /* Tight contact shadow */
    0 6px 16px -4px rgba(15, 23, 42, 0.04); /* Soft ambient diffusion */
}
```

### Multi-layer shadow construction
Never use a single large `box-shadow` with high opacity. Build shadows in 2–3 physical layers:
1. **Contact shadow (tight & darkest):** `0 1px 2px` with low blur, grounds the object against the surface beneath.
2. **Ambient shadow (medium & soft):** `0 4px 12px` with negative spread (`-2px`), simulates overhead diffused room light.
3. **Floating shadow (overlays/modals only):** `0 16px 32px -8px`, reserved strictly for modals, menus, detached drawers.

- **Shadow tinting:** never use pure black `rgba(0,0,0,x)` over warm or cool light backgrounds. Tint shadows toward the darkest shade of your neutral palette (deep slate or warm umber) at 3–8% opacity.

### Specular rim lighting (the secret to tactile depth)
Human designers make dark UIs and dark primary buttons feel machined rather than flat by simulating overhead light hitting the top edge of a surface:

```css
/* Dark Mode Card with Top-Edge Light Catch */
.surface-card-dark {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.03) 0%, rgba(255, 255, 255, 0.00) 100%), var(--surface-base);
  border: 1px solid rgba(255, 255, 255, 0.07);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.06), /* Top specular highlight */
    0 4px 16px rgba(0, 0, 0, 0.35);          /* Grounded dark drop */
}

/* Tactile Dark Primary Button (Works in BOTH Light and Dark Modes) */
.btn-primary-tactile {
  background: linear-gradient(180deg, #27292E 0%, #141518 100%);
  border: 1px solid rgba(255, 255, 255, 0.12);
  box-shadow:
    inset 0 1px 0.5px rgba(255, 255, 255, 0.18), /* Subtle beveled top rim */
    0 1px 2px rgba(0, 0, 0, 0.25),
    0 4px 10px -2px rgba(0, 0, 0, 0.20);
}
```

### Restraint with gradients & glows
- **Never** apply vibrant neon outer glows (`box-shadow: 0 0 25px purple`) to cards or buttons.
- **Do** use ultra-subtle ambient radial washes (large blur, low opacity, soft color transition) sparingly inside focal hero modules (e.g., a subtle warm dome behind a weather metric or an understated radial sheen behind an AI brand mark) to introduce warmth without hurting readability.
