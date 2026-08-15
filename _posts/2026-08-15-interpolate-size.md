---
title: "interpolate-size"
date: 2026-08-15
categories: ["CSS"]
tags: ["interpolate-size"]
layout: single
source: "https://drafts.csswg.org/css-values-5/#propdef-interpolate-size"
---

Animating an element from a fixed size to an intrinsic size has traditionally been difficult. A transition such as `height: 0` to `height: auto` normally cannot interpolate smoothly because `auto` is a sizing keyword rather than a numeric value.

The `interpolate-size` property lets authors opt in to interpolation between a `<length-percentage>` value and an intrinsic sizing keyword. This makes common effects such as expanding panels possible without measuring content in JavaScript or guessing a maximum height.

`interpolate-size` is defined in the CSS Values and Units Module Level 5, which is a CSS Working Group Editor’s Draft. It is still an evolving standards feature rather than a finalized Recommendation.

The property currently accepts two values:

- `numeric-only`, the initial value, preserves the traditional behavior.
- `allow-keywords` permits interpolation when one endpoint is a `<length-percentage>` and the other is an intrinsic sizing keyword supported by that sizing property.

The property is inherited, so it can be enabled for an entire document:

```css
:root {
  interpolate-size: allow-keywords;
}

.panel {
  height: 3rem;
  overflow: clip;
  transition: height 250ms ease;
}

.panel:hover,
.panel:focus-within {
  height: auto;
}
```

Here, the panel transitions between a fixed `height` and its automatic height. Because the final size comes from layout, it can adapt to changing text, fonts, localization, responsive widths, or dynamically inserted content. That makes `interpolate-size` useful today for disclosures, navigation panels, expandable cards, and other interfaces whose content size is not known in advance.

There are important caveats. Enabling `allow-keywords` does not make every pair of sizing keywords interpolable: the defined opt-in concerns a numeric size on one side and an intrinsic sizing keyword on the other. Layout is also recalculated as the intrinsic size changes, so developers should test performance when animating large or complex subtrees.

Implementation support can vary, and the specification may continue to change. Treat the feature as a progressive enhancement and test the browsers relevant to your project. You can isolate enhanced styling with a feature query:

```css
@supports (interpolate-size: allow-keywords) {
  :root {
    interpolate-size: allow-keywords;
  }
}
```

Without support, the interface should remain usable even if the size change is not smoothly interpolated.

Further reading: [CSS Values and Units Level 5 — `interpolate-size`](https://drafts.csswg.org/css-values-5/#propdef-interpolate-size)
