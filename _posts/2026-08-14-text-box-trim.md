---
title: "text-box-trim"
date: 2026-08-14
categories: ["CSS"]
tags: ["text-box-trim"]
layout: single
source: "https://drafts.csswg.org/css-inline-3/#text-box-trim"
---

`text-box-trim` removes metric-derived space at the block-start and/or block-end edges of a text box. That extra space comes from font metrics and line-height calculations: it is useful for readable line layout, but it can make text appear slightly misaligned inside buttons, cards, banners, and other tightly designed components.

The property is defined in CSS Inline Layout Module Level 3, which remains a draft CSS Working Group specification rather than a finalized Recommendation. Its details can therefore evolve.

`text-box-trim` selects which edges are trimmed:

- `none` performs no trimming.
- `trim-start` trims the block-start edge.
- `trim-end` trims the block-end edge.
- `trim-both` trims both edges.

It works with `text-box-edge`, which selects the font-relative edges used for trimming. For example:

```css
.heading {
  text-box-trim: trim-both;
  text-box-edge: cap alphabetic;
}
```

Here, the upper edge is aligned to the font’s cap-height edge, while the lower edge is aligned to its alphabetic baseline. This can make a heading’s visible letterforms align more naturally with surrounding borders, backgrounds, images, or spacing.

The feature is especially useful in design systems. Developers have traditionally compensated for apparent space around text with one-off padding values, negative margins, transforms, or font-specific adjustments. Those techniques are fragile: changing the font, weight, language, or line-height can invalidate the carefully chosen numbers. `text-box-trim` expresses the intended typographic alignment directly and lets the browser use the font’s metrics.

Trimming affects the outer edges of the text box; it is not a general replacement for `line-height` and does not simply remove spacing between every line. Glyph ink may also extend beyond a selected metric—for example, because of accents, decorative shapes, or descenders—so test with the actual fonts and content your interface uses.

Browser implementation and interoperability may be incomplete. Check current compatibility information for your target browsers rather than assuming universal support. Unsupported declarations are ignored, leaving the normal text-box metrics as a usable fallback. For progressive enhancement, `@supports (text-box-trim: trim-both)` can be used when alternative spacing needs to be applied conditionally.

Further reading: [CSS Inline Layout Module Level 3 — `text-box-trim`](https://drafts.csswg.org/css-inline-3/#text-box-trim)
