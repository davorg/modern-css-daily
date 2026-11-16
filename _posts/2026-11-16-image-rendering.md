---
title: "image-rendering"
date: 2026-11-16
categories: ["CSS"]
tags: ["image-rendering"]
layout: single
source: "https://drafts.csswg.org/css-images-3/#the-image-rendering"
---

`image-rendering` tells the browser which qualities to prioritize when an image is scaled. It does not select one mandatory resampling algorithm; instead, it provides a hint about whether smoothing or visible pixel boundaries matter most.

The property is defined in CSS Images Module Level 3. The linked CSSWG document is a current draft, so implementations may differ in how faithfully they interpret each hint.

The specification defines four values:

- `auto` leaves the scaling algorithm to the browser.
- `smooth` favors algorithms that smooth colors, making it appropriate for photographs and gradients.
- `high-quality` has the same general goal as `smooth`, but asks the browser to prioritize higher-quality scaling when resources are constrained.
- `pixelated` uses nearest-neighbor scaling, or a similar algorithm, when enlarging an image. When reducing an image, it behaves like `auto`.

A minimal example for enlarging pixel art is:

```html
<img class="sprite" src="sprite.png" alt="Game character" width="32" height="32">
```

```css
.sprite {
  width: 256px;
  height: 256px;
  image-rendering: pixelated;
}
```

Without `pixelated`, enlarging a tiny sprite may blend neighboring colors and produce blurry edges. With it, the browser preserves the block-like appearance expected from pixel art. The property is therefore useful for retro game graphics, low-resolution icons, image editors, maps made from discrete tiles, and scaled `<canvas>` output. Conversely, `smooth` or `high-quality` can express that continuous tones matter more than hard pixel boundaries.

There are important caveats. `image-rendering` is a rendering hint, not a guarantee of a specific filter or identical output across browsers and operating systems. It cannot restore detail missing from the source image, and `high-quality` does not guarantee that scaling will look noticeably different from `smooth`.

`pixelated` is specifically useful for enlargement. For the most regular-looking blocks, scale pixel art by an integer multiple of its original dimensions; non-integer scaling can produce uneven pixel sizes. Also remember that the property is inherited, so applying it to a container can affect images in its descendants. Use a targeted selector when only particular assets require special treatment.

As with any rendering-sensitive feature, test the result in the browsers relevant to your project rather than assuming identical output.

Further reading: [CSS Images Module Level 3: `image-rendering`](https://drafts.csswg.org/css-images-3/#the-image-rendering)
