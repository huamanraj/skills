# Interaction States & Motion Physics

Read during Stage 6 (states, motion, accessibility) of the pipeline in SKILL.md.

The difference between a static mockup and a production interface is that every element answers every interaction. Default-only styling is unfinished work.

## 1. The complete state set

Every interactive element ships all applicable states, designed deliberately:

| State | Rule |
| :--- | :--- |
| **Default** | The quiet baseline; everything else steps away from it and returns to it. |
| **Hover** | Subtle: a 2-4% luminance shift, a hairline border appearing, or a 1-2px lift. Never a color flood or a scale-up beyond ~1.02. |
| **Focus** | Always visible for keyboard users: a crisp 2px outline or ring in the accent color, offset 2px, never removed (`outline: none` is banned without a replacement). Distinct from hover. |
| **Pressed / active** | Immediate tactile feedback: slight darken, 1px sink, or shadow compression. Confirms the click registered. |
| **Disabled** | Reduced opacity (~40-50%), no hover response, `cursor: not-allowed`. Explain why when the reason is not obvious (a tooltip or hint text). |
| **Loading** | Show progress on the control itself (spinner replacing the label, label plus spinner, or progress fill) and block repeat submission. Never leave the UI frozen after a click. |
| **Skeleton / pending content** | Use skeleton placeholders shaped like the incoming content for loads over ~300ms. Reserve spinners for short, indeterminate waits and button-level feedback. |

Forms additionally need **validating**, **error**, and **success** states per field and per form (see `content-and-components.md`).

## 2. Async feedback without layout shift

State changes must not move the page under the user's eyes:

- Reserve space for content that loads later: fixed-height media (`aspect-ratio`), skeleton blocks sized to the final layout, min-height on async regions.
- Inline validation messages appear in reserved or inserted space below the field, never by pushing the next field down mid-typing; validate on blur or submit, not on every keystroke.
- Toasts and notifications overlay the layout (fixed position); they never push content.
- Cumulative layout shift is a defect: if the page jumps when data arrives, the async region needed a placeholder.

## 3. Transition timing and easing

Motion should feel instantaneous but physical:

| Motion | Duration | Easing |
| :--- | :--- | :--- |
| Micro (hover, focus, pressed, color/opacity) | 100-200ms | `ease-out` |
| Surface (dropdowns, tooltips, popovers appearing) | 150-250ms | `ease-out` or a soft custom cubic-bezier |
| Large (modals, drawers, page transitions) | 200-350ms | `ease-out` on entry, `ease-in` on exit |

- Enter quickly, leave quickly; nothing in a professional UI animates longer than ~400ms.
- No bounce, spring, or overshoot easing in productivity software. Save playful physics for consumer moments that earn it.
- Animate `transform` and `opacity` only; animating layout properties (`width`, `height`, `top`, `margin`) causes jank.

## 4. Hover movement restraint

Lift, never leap. A card hover is a 1-2px translateY plus a whisper of extra shadow. If a hover effect is noticeable from across the room, it is too loud for minimal UI.

## 5. Reduced motion

Honor `prefers-reduced-motion`: replace movement with instant or short opacity-only transitions. Never disable focus indicators as part of simplification.

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## 6. Keyboard interaction

Every action available to a pointer is available to a keyboard: menus open and navigate with arrows and Escape, dialogs trap focus and close on Escape, lists support arrow navigation where pattern-appropriate. See `accessibility.md` for the full requirements.
