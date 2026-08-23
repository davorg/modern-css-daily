---
title: "forced-color-adjust"
date: 2026-08-23
categories: ["CSS"]
tags: ["forced-color-adjust"]
layout: single
source: "https://www.w3.org/TR/css-color-adjust-1/#forced-color-adjust-prop"
---

`forced-color-adjust` controls whether the browser may alter an element’s colors when a forced-colors mode is active. Such modes often replace author-defined colors with a limited, user-selected palette to improve readability and contrast.

The property is defined in the W3C’s CSS Color Adjustment Module Level 1, currently published as a Candidate Recommendation Draft rather than a final Recommendation.

Its initial value is `auto`, which allows the user agent to make its normal forced-color adjustments. Setting it to `none` opts an element out of those adjustments:

```html
<span class="swatch" aria-label="Red"></span>
```

```css
.swatch {
  display: inline-block;
  width: 2rem;
  height: 2rem;
  background-color: red;
  border: 1px solid CanvasText;
  forced-color-adjust: none;
}
```

This example preserves the swatch’s red background because the exact color is the content being presented. The accessible label ensures that color is not the only way the information is conveyed.

The property also accepts `preserve-parent-color`. In forced-colors mode, this preserves an inherited parent color in the circumstances defined by the specification; otherwise, it behaves like `auto`. This value is particularly relevant where an element needs to retain its parent’s adjusted color rather than receive an independent adjustment.

The feature is useful today because author styles can behave unexpectedly under forced colors. Backgrounds may be replaced, decorative effects may disappear, and foreground colors may be remapped. Usually this is desirable: the browser is honoring the user’s accessibility preferences. However, selective opt-outs can make sense for color previews, gradients used as data, certain image-like controls, or other elements whose colors carry essential meaning.

Use `none` sparingly. It can reduce contrast or make content unreadable in the exact environment designed to help the user. The property is inherited, so applying it to a container can also affect descendants. Scope it narrowly, test with forced colors enabled, and provide text, borders, icons, or other non-color cues. The `forced-colors` media feature can be used alongside it when a component needs additional mode-specific styling.

Implementation details can vary across browsers and platforms, so verify behavior in the browsers and operating-system modes your project supports rather than assuming identical color substitutions.

Further reading: [CSS Color Adjustment Module Level 1 — `forced-color-adjust`](https://www.w3.org/TR/css-color-adjust-1/#forced-color-adjust-prop)
