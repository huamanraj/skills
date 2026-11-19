# Image Art Direction & Media Composition

Read during Stage 5 (page composition) of the pipeline in SKILL.md.

Imagery is a structural element of the composition, not filler. The wrong image, crop, or weight distribution undoes careful surface and type work.

## 1. Photography selection

- One consistent grade per product: match warmth, contrast, and saturation across every image on a page. A mismatched set reads as clip art.
- Avoid stock clichés (handshakes, pointing-at-laptop teams, glowing blue brain illustrations). Prefer real product UI, real environments, or quiet abstract textures.
- Match surface polarity: matte, dark-toned assets in dark interfaces; soft, light assets in light ones (see the embedded media rules in `components-and-icons.md`).
- No imagery that fights the focal hierarchy: the hero image supports the headline, it does not compete with it.

## 2. Crops and object positioning

- Crop with intent: decide what the image is about and cut to that. A portrait used as a wide banner becomes an extreme face crop; choose a different crop, a different image, or a different layout instead of stretching.
- Use `object-fit: cover` with deliberate `object-position` (for example `object-position: center 30%` to keep faces in frame) for every fixed-ratio image slot.
- Keep one aspect ratio per context: all avatars identical, all card thumbnails identical, all hero media identical. Mixed ratios in one grid read as accidents.
- Test the crop at every breakpoint: a crop that works at 1440px may decapitate the subject at 375px. Adjust `object-position` per breakpoint or serve a different crop.

## 3. Image-to-text balance

- Split layouts hold a stable ratio (60/40 or 50/50); media does not balloon wider than the content it accompanies.
- Text over imagery requires a guaranteed-contrast treatment: a gradient scrim (dark at the text edge), a solid backing surface, or an overlaid panel. Verify the result against the contrast floors in `accessibility.md`; a subtle image change must never break readability.
- Captions and labels near media use the quiet metadata treatment (text-tertiary, small size), never badges glued onto the image.

## 4. Visual consistency across the page

- Images align to the same rails as everything else: media edges share the grid's left and right coordinates.
- Radius on media follows the concentric rule for its container (see `spacing-and-layout.md`), plus a 1px inner border on light images over light surfaces so edges never bleed.
- Icons are not imagery and imagery is not icons: never substitute an emoji or a stock illustration where an interface icon belongs.

## 5. Performance as design

- Serve responsive sizes with `srcset`/`sizes`; never ship a 3000px photo to a 375px viewport.
- Declare `width`/`height` or `aspect-ratio` on every image so the layout does not jump while loading (see layout stability in `visual-qa.md`).
- Lazy-load below-the-fold media; preload the single hero image.
- Prefer modern formats (WebP/AVIF) with sensible quality; a beautiful page that loads in six seconds reads as broken.
