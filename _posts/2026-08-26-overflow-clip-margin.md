---
title: "overflow-clip-margin"
date: 2026-08-26
categories: ["CSS"]
tags: ["overflow-clip-margin"]
layout: single
source: "https://drafts.csswg.org/css-overflow-3/#propdef-overflow-clip-margin"
---

`overflow-clip-margin` lets an element using `overflow: clip` paint slightly beyond its normal clipping boundary. The resulting boundary is called the *overflow clip edge*.

By default, clipped overflow is cut off at the element’s clipping edge. A non-negative `overflow-clip-margin` length moves that edge outward, creating a small painting allowance without changing the element’s dimensions or affecting layout.

```css
.thumbnail {
  overflow: clip;
  overflow-clip-margin: 8px;
}
```

Here, overflowing content may remain visible for up to `8px` beyond the usual clip edge before being clipped. The property only has an effect when the relevant `overflow` value is `clip`; it does not change how `hidden`, `auto`, or `scroll` behave.

This is useful for components that need strict overflow clipping but also have visual details that extend slightly outside their box. Examples include shadows, outlines, transformed descendants, or decorative effects near an edge. Without an overflow clip margin, those details can be cut off abruptly. Expanding the clip edge can preserve them while still preventing content from painting indefinitely outside the component.

Unlike adding padding, `overflow-clip-margin` does not move the content or make the box larger. It also does not reserve space around the element. Nearby layout therefore remains unchanged, and any allowed painting can overlap surrounding content.

The property is defined in CSS Overflow Module Level 3. That module is still a draft, so authors should treat the specification as subject to change rather than as a finalized standard. Avoid relying on assumptions from older articles or experimental implementations; consult the current grammar when using anything beyond a simple length.

Browser support should also be verified for the browsers required by your project. Do not assume that support for `overflow: clip` automatically implies support for `overflow-clip-margin`. A basic declaration generally degrades safely because unsupported properties are ignored, but the visual result will use the ordinary clip edge instead. Test effects such as shadows and transformed descendants directly, since the property expands the clipping boundary for painting rather than selectively exempting one effect.

For progressive enhancement, feature queries can isolate the behavior:

```css
@supports (overflow-clip-margin: 8px) {
  .thumbnail {
    overflow: clip;
    overflow-clip-margin: 8px;
  }
}
```

Further reading: [CSS Overflow Module Level 3 — `overflow-clip-margin`](https://drafts.csswg.org/css-overflow-3/#propdef-overflow-clip-margin)
