---
title: "overflow-block"
date: 2026-11-23
categories: ["CSS"]
tags: ["overflow-block"]
layout: single
source: "https://drafts.csswg.org/css-overflow-3/#propdef-overflow-block"
---

`overflow-block` controls overflow along an element’s **block axis**. In the common `horizontal-tb` writing mode, that is the vertical axis. In vertical writing modes, the block axis is horizontal. This makes `overflow-block` the writing-mode-aware alternative to choosing `overflow-x` or `overflow-y` directly.

The property accepts the keywords `visible`, `hidden`, `clip`, `scroll`, and `auto`. For example, this creates a scrolling region when the content exceeds the panel’s block size:

```css
.panel {
  block-size: 12rem;
  overflow-block: auto;
}
```

With `auto`, the user agent provides a scrolling mechanism when the content overflows in the block direction. The other values follow the overflow model: `visible` allows overflow to remain visible, `hidden` clips it without presenting a scrolling interface, `clip` clips it and forbids scrolling, and `scroll` provides a scrolling mechanism regardless of whether content currently overflows.

The main benefit is adaptability. A component written with `overflow-block` can change its `writing-mode` without needing to swap between `overflow-y` and `overflow-x`. That is particularly useful for multilingual sites, vertical typography, reusable design-system components, and layouts that already use logical properties such as `block-size`, `margin-inline`, and `padding-block`.

`overflow-block` is defined in CSS Overflow Module Level 3. The linked CSS Working Group document is an Editor’s Draft, so the feature is part of an evolving draft standard rather than a finalized W3C Recommendation. No precise “introduction date” should be inferred from that status.

There are several practical caveats. Browser implementation may vary, so check current compatibility information and test in the browsers your project supports. If a fallback is necessary, a physical-axis property such as `overflow-y` may be reasonable for layouts known to use horizontal writing, but it is not a fully logical equivalent in every writing mode.

Also, overflow requires a constraint: if an element can keep growing in its block direction, there may be nothing to scroll or clip. Finally, overflow values on the two axes interact at computed-value time: when one axis is neither `visible` nor `clip`, `visible` on the other axis computes to `auto`, while `clip` computes to `hidden`. Test both axes when precise clipping behavior matters.

Further reading: [CSS Overflow Module Level 3 — `overflow-block`](https://drafts.csswg.org/css-overflow-3/#propdef-overflow-block)
