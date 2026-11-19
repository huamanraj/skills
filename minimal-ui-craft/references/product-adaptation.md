# Product-Specific Design Adaptation

Read during Stage 0 (product identification) of the pipeline in SKILL.md.

The rules in this skill are universal, but their measurements are calibrated to neutral SaaS interfaces. Before choosing tokens or components, classify the product and adjust the priorities. Applying dashboard instincts to a landing page (or the reverse) produces the generic look this skill exists to prevent.

## 1. Classify the interface

| Interface type | Design priorities | What changes concretely |
| :--- | :--- | :--- |
| **SaaS dashboard** | Information density, scanning, alignment, clear status | Tighter spacing and smaller type (13-14px body), compact 32-36px controls, restrained imagery, persistent navigation chrome. |
| **Marketing landing page** | Storytelling, emotional imagery, headline composition, clear CTA | Larger display type (clamp-scaled), generous whitespace, art-directed media, one CTA repeated, varied section composition (see `page-composition.md`). |
| **E-commerce** | Product photography, comparison, trust, conversion | Imagery leads (consistent ratios, zoom/detail views), price and CTA always visible, trust signals near purchase actions, dense spec content pushed to accordions. |
| **Mobile application** | Touch targets, thumb reach, navigation, content priority | 44px+ targets, primary actions in thumb range (bottom half), bottom navigation or sheets over sidebars, one task per screen. |
| **Editorial website** | Reading rhythm, typography, imagery, long-form layout | Serif-led or editorial pairing, 60-72ch measure, 1.6+ body line-height, pull quotes and captions, minimal chrome while reading. |
| **Developer tool** | Dense information, code readability, keyboard interaction | Monospace for code/paths/IDs, 12-13px density tolerated, full keyboard coverage and visible focus, docs-grade table and list craft. |

## 2. Adapt the measurements, keep the principles

What flexes per product type:

- **Color ratio:** the 90/8/2 neutral foundation is a SaaS default. Editorial and marketing products can carry more brand color and richer imagery; keep the discipline (accents reserved for actions and focal points) rather than the exact numbers.
- **Density:** 25-35% interior negative space suits marketing cards and empty states; data tables and compact professional controls pack tighter. Set density by purpose.
- **Type scale and tracking:** display sizes and tracking are tuned per product voice and per rendered font, never copied blindly from the table in `typography.md`.
- **Motion budget:** productivity surfaces stay nearly still; consumer and marketing surfaces may earn slightly more expressive transitions, within the restraint rules in `interaction-and-motion.md`.
- **Emoji and illustration:** banned as default UI chrome, but a playful consumer product can deliberately choose them as part of its voice. The choice must be a system, not an accident.

What never flexes: contrast floors, keyboard access, focus visibility, alignment rails, state completeness, and visual verification.

## 3. Mixed products

Real products mix types (a SaaS app with a marketing site, an e-commerce admin). Classify per surface, not per company: the checkout page follows e-commerce priorities, the admin panel follows dashboard priorities, the homepage follows landing-page priorities. Keep the token system shared so the surfaces still feel like one product.
