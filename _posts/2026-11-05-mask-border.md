---
title: "mask-border"
date: 2026-11-05
categories: ["CSS"]
tags: ["mask-border"]
layout: single
source: "https://www.w3.org/TR/css-masking-1/#the-mask-border"
---

`mask-border` uses an image as a mask around an element’s border box. Like `border-image`, it divides the source into nine regions: four corners, four edges, and a center. The corners are placed at the corners of the mask border area, while the edge regions can be stretched, repeated, rounded, or spaced. The optional `fill` keyword preserves the center region.

Unlike `border-image`, the source does not paint visible decoration. Its alpha channel or luminance controls which parts of the element remain visible. This makes `mask-border` suitable for irregular frames, perforated edges, fades, and other effects that would otherwise require extra elements or carefully positioned overlays.

The feature is defined in CSS Masking Module Level 1. The linked W3C specification is published as a Candidate Recommendation Draft rather than a final W3C Recommendation.

A minimal example using the shorthand is:

```css
.badge {
  padding: 1.5rem;
  color: white;
  background: royalblue;

  mask-border:
    url("frame-mask.png") 30 fill / 18px / 0 round alpha;
}
```

Here, `frame-mask.png` is the mask source. The value `30` slices 30 units from each side of the source image. `fill` includes its center region, `18px` sets the mask-border width, `0` adds no outset, `round` tiles the edge regions while adjusting their size to fit, and `alpha` uses the image’s alpha channel to calculate the mask.

This nine-slice model is useful for responsive components because the corners can retain their shape while the edges adapt to the element’s dimensions. One source asset can therefore mask buttons, panels, or cards of several sizes without requiring a separately rendered image for each size.

The main caveat is implementation support. `mask-border` is not reliably interoperable across major browsers, so check current compatibility information and test in every browser you support. It is generally best treated as a progressive enhancement, with an ordinary rectangular presentation as the fallback.

Also note that the `mask` shorthand resets the `mask-border-*` properties to their initial values. If both are used in the same rule, declaration order matters: place `mask-border` after `mask`, or use the relevant longhand properties deliberately.

Further reading: [CSS Masking Module Level 1 — Mask Borders](https://www.w3.org/TR/css-masking-1/#the-mask-border)
