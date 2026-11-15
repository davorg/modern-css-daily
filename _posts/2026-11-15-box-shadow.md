---
title: "box-shadow"
date: 2026-11-15
categories: ["CSS"]
tags: ["box-shadow"]
layout: single
source: "https://www.w3.org/TR/css-backgrounds-3/#box-shadow"
---

`box-shadow` paints one or more shadows around an element’s box. It can create elevation, outlines, soft borders, or recessed surfaces without image assets or extra markup. The property is defined in the W3C’s standards-track **CSS Backgrounds and Borders Module Level 3** specification; it is not a vendor-specific extension. The document header provides its current formal publication status.

A minimal example:

```css
.card {
  box-shadow: 0 0.5rem 1rem 0 rgba(0, 0, 0, 0.2);
}
```

The four lengths represent the horizontal offset, vertical offset, blur radius, and spread distance. Here, the shadow is directly below the box, blurred by `1rem`, with no spread. The color is a partially transparent black.

Positive offsets move the shadow right and down; negative offsets move it left and up. The blur radius must not be negative, while the spread distance may be negative. If the color is omitted, it defaults to `currentColor`.

Multiple shadows can be supplied as a comma-separated list. They are painted front to back, so the first shadow appears on top of later ones. Adding the `inset` keyword changes an outer drop shadow into an inner shadow:

```css
.field {
  box-shadow: inset 0 0 0.25rem rgba(0, 0, 0, 0.3);
}
```

This flexibility makes `box-shadow` useful for modern interface components such as cards, dialogs, buttons, and form controls. It also follows rounded corners created with `border-radius`, making it practical for common component shapes.

There are important caveats. Shadows are visual effects: they do not affect layout or reserve space around an element, so they may overlap nearby content. Ancestor clipping can also prevent an outward shadow from being fully visible. The specification does not mandate one exact blur algorithm, so subtle rendering differences are possible between implementations.

Large blurred shadows—especially when repeated across many moving elements—may require additional painting work. Profile the actual interface rather than assuming the cost is negligible. Also, do not rely on a shadow alone to communicate essential state or focus; provide accessible visual cues that remain understandable when decorative effects are unavailable or difficult to perceive.

Further reading: [CSS Backgrounds and Borders Module Level 3 — `box-shadow`](https://www.w3.org/TR/css-backgrounds-3/#box-shadow)
