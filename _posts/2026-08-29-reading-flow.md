---
title: "reading-flow"
date: 2026-08-29
categories: ["CSS"]
tags: ["reading-flow"]
layout: single
source: "https://drafts.csswg.org/css-display-4/#reading-flow-property"
---

CSS layout can make content appear in an order that differs from its source order. Grid placement, flexbox direction, and the `order` property can all create this mismatch. The `reading-flow` property lets authors specify the order in which items inside a block, flex, or grid container participate in reading order.

That reading order is relevant to non-visual presentation, such as speech, and to sequential focus navigation. Importantly, `reading-flow` does not move elements in the DOM or change their visual placement. It provides an ordering model for user agents and accessibility tools.

For example, a grid can follow its visual rows:

```css
.cards {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  reading-flow: grid-rows;
}
```

Here, `grid-rows` establishes a row-by-row reading flow based on the grid layout. The specification also defines values for other ordering strategies, including column-by-column grid order and flex layout order. The initial value is `normal`.

This is useful because responsive interfaces often cannot maintain one source order that matches every possible visual arrangement. A card grid might move a featured item, while a flex container might reverse direction at a breakpoint. In supporting implementations, `reading-flow` can help keep sequential navigation and non-visual presentation aligned with the resulting layout. Because unsupported browsers ignore an unrecognized declaration, it can also be introduced as a progressive enhancement.

There are important caveats. `reading-flow` is defined in CSS Display Module Level 4, which is a working draft rather than a finalized web standard. Its details may still change, and implementation support is not universal. Support for parsing the property also does not necessarily guarantee identical behavior across browsers, accessibility APIs, and assistive technologies, so test the combinations relevant to your users.

The property is also not a substitute for meaningful document structure. Source order remains important for unsupported software, content without CSS, copying and serialization, and other consumers of the DOM. Prefer a logical source order whenever possible, and use `reading-flow` when layout genuinely requires a different presentation order. Avoid relying on it to repair arbitrary or confusing markup.

Further reading: [CSS Display Module Level 4 — `reading-flow`](https://drafts.csswg.org/css-display-4/#reading-flow-property)
