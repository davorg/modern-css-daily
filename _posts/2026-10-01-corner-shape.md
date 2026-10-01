---
title: "corner-shape"
date: 2026-10-01
categories: ["CSS"]
tags: ["corner-shape"]
layout: single
source: "https://drafts.csswg.org/css-borders-4/#corner-shaping"
---

`corner-shape` lets CSS authors control the contour used for an element’s corners. While `border-radius` determines the size of each corner, `corner-shape` determines how the corner transitions between its adjoining edges.

The default value, `round`, preserves the familiar elliptical corners produced by `border-radius`. The specification also defines shapes such as `squircle`, `bevel`, `notch`, `scoop`, and `square`, as well as a `superellipse()` function for more direct control over the curve.

A minimal example looks like this:

```css
.card {
  border: 1px solid;
  border-radius: 2rem;
  corner-shape: squircle;
}
```

Here, `border-radius` provides the corner dimensions, while `corner-shape` changes those corners from ordinary rounded corners to squircles. A nonzero corner radius is important: if there is no rounded-corner area to shape, `corner-shape` has no visible effect.

This separation is useful because many interface designs need more than conventional rounded rectangles. A squircle can give cards and controls a softer, more continuous appearance. Beveled corners can support geometric or technical visual styles, while scooped and notched corners can create cutout-like treatments without SVG, masks, or generated elements.

The feature is also suitable for progressive enhancement. In a browser that does not recognize `corner-shape`, the declaration is ignored, but the accompanying `border-radius` still provides a conventional rounded-corner fallback. That makes it possible to experiment with distinctive shapes without making the basic component unusable.

There are important caveats. `corner-shape` is defined in the CSS Borders and Box Decorations Module Level 4 draft; it is not a finalized W3C Recommendation, so its details may still change. Browser implementation is not universal, and support should be checked against the browsers required by a project rather than assumed. Test interactions with borders, backgrounds, clipping, and nearby content as well: unusual corner contours may expose design assumptions that ordinary rounded corners do not.

For production use, treat `corner-shape` as an enhancement, keep a sensible `border-radius` fallback, and verify both the enhanced and fallback appearances.

Further reading: [CSS Borders and Box Decorations Level 4 — Corner Shaping](https://drafts.csswg.org/css-borders-4/#corner-shaping)
