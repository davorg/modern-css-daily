---
title: "sibling-count()"
date: 2026-11-27
categories: ["CSS"]
tags: ["sibling-count()"]
layout: single
source: "https://drafts.csswg.org/css-values-5/#tree-counting"
---

`sibling-count()` is a CSS tree-counting function that returns the number of element children in the current element’s parent. The count includes the element being styled, while text nodes and comments do not contribute. Its result is an integer, so it can participate in calculations used by CSS properties.

For example, a flex container can divide its width equally among however many cards it contains:

```css
.cards {
  display: flex;
}

.cards > .card {
  flex: 1 1 0; /* fallback */
  flex: 0 0 calc(100% / sibling-count());
}
```

If `.cards` contains four `.card` elements, `sibling-count()` resolves to `4` for each card, producing a `25%` flex basis. Add or remove a card and the calculation follows the new element count without requiring an extra class, custom property, or JavaScript update.

This is useful for interfaces whose structure is generated dynamically: navigation bars, tab lists, dashboards, rating controls, and component collections. CSS selectors can match elements according to their position or surrounding structure, but they do not normally expose the total number of siblings as a numeric value. `sibling-count()` makes that number available directly to property calculations.

The function is defined in the CSS Values and Units Level 5 specification. That specification is still a draft rather than a finalized Recommendation, so the feature’s details can change as the standard develops.

Browser support should not be assumed to be universal. Check the requirements of your target browsers and test the actual declarations you intend to ship. Where the function is used for enhancement rather than essential presentation, place a conventional declaration first, as in the example. A browser that cannot use the later declaration can retain the fallback. Also remember that the function counts all element children of the parent, not only siblings matching the selector. In the example, unrelated element children inside `.cards` would therefore affect the result.

Further reading: [CSS Values and Units Level 5 — Tree Counting Functions](https://drafts.csswg.org/css-values-5/#tree-counting)
