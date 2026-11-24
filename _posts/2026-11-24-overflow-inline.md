---
title: "overflow-inline"
date: 2026-11-24
categories: ["CSS"]
tags: ["overflow-inline"]
layout: single
source: "https://drafts.csswg.org/css-overflow-3/#propdef-overflow-inline"
---

`overflow-inline` controls how a container handles content that overflows along its **inline axis**. In the common `horizontal-tb` writing mode, that is the horizontal axis. In vertical writing modes, the inline axis is vertical.

The property is the logical-axis counterpart to choosing `overflow-x` or `overflow-y` based on the writing mode. It is defined in CSS Overflow Module Level 3, which remains a draft specification rather than a finalized W3C Recommendation.

A minimal example:

```css
.code-row {
  inline-size: 24rem;
  white-space: nowrap;
  overflow-inline: auto;
}
```

Here, `.code-row` can provide a scrolling mechanism when its unwrapped content is wider than its inline size. If the component is used with a vertical writing mode, the same declaration handles overflow on the corresponding vertical inline axis instead.

The property accepts the overflow keywords defined by the specification:

- `visible` leaves overflow visible.
- `hidden` clips overflow and does not provide a user-facing scrolling mechanism, although programmatic scrolling is still possible.
- `clip` clips content at the overflow clip edge and forbids scrolling.
- `scroll` creates a scroll container whether or not content currently overflows.
- `auto` lets the user agent provide a scrolling mechanism when appropriate.

This is useful for components designed around logical properties such as `inline-size`, `margin-inline`, and `padding-inline`. Instead of assuming that text always flows horizontally and selecting `overflow-x`, a component can describe its behavior in terms of the writing axis. That makes styles more adaptable to vertical typography, internationalized layouts, and reusable design systems.

There are important caveats. Browser support should be checked for the environments your project targets; do not assume that support for `overflow-x` and `overflow-y` implies support for `overflow-inline`. When a fallback is needed, place the appropriate physical property first:

```css
.code-row {
  overflow-x: auto;       /* Fallback for horizontal writing modes */
  overflow-inline: auto;
}
```

That fallback is only semantically equivalent when the inline axis is horizontal. A component that genuinely switches writing modes may need writing-mode-specific physical fallbacks.

Also, overflow requires a constrained container before there is anything to clip or scroll, and the property applies to block, flex, and grid containers—not arbitrary inline boxes. Its behavior can also interact with overflow settings on the other axis, so test combinations rather than treating each axis as entirely independent.

Further reading: [CSS Overflow Module Level 3: `overflow-inline`](https://drafts.csswg.org/css-overflow-3/#propdef-overflow-inline)
