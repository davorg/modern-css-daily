---
title: "sibling-index()"
date: 2026-09-08
categories: ["CSS"]
tags: ["sibling-index()"]
layout: single
source: "https://drafts.csswg.org/css-values-5/#funcdef-sibling-index"
---

`sibling-index()` is a CSS value function that returns an element’s position among its element siblings. The first element child has an index of `1`, the second `2`, and so on. Text nodes and comments are not counted.

The function takes no arguments and produces an `<integer>`, so it can be used directly in integer-valued properties or as part of a calculation:

```css
.stack > * {
  position: relative;
  z-index: sibling-index();
}
```

Here, later children receive higher `z-index` values. The index comes from document-tree order and updates when elements are inserted, removed, or moved.

`sibling-index()` is defined in CSS Values and Units Module Level 5. That module is currently an Editor’s Draft rather than a finished Recommendation, so the feature and its details may still change.

The function is useful because sibling position often needs to become data. Staggered animations, layered cards, stepped spacing, and generated visual variation traditionally require repeated `:nth-child()` rules, server-generated classes, inline custom properties, or JavaScript. With `sibling-index()`, CSS can derive the number directly from the document structure.

For example, a supporting browser could calculate delays from each item’s position:

```css
.list > li {
  animation-delay: calc((sibling-index() - 1) * 80ms);
}
```

Subtracting `1` gives the first item a zero-second delay.

There are important caveats. Browser support is not universal, so check the compatibility requirements of your project and provide a fallback when the result affects usability. A normal earlier declaration works well for many cases:

```css
.list > li {
  animation-delay: 0ms;
  animation-delay: calc((sibling-index() - 1) * 80ms);
}
```

Browsers that do not accept the second declaration retain the fallback.

Also, the index covers all element siblings, not only siblings matching the selector that contains the declaration. If a list mixes several element types or classes, those elements still affect the returned number. The function follows tree order rather than a layout’s visual rearrangement, so properties such as flex or grid ordering should not be treated as changing the sibling index.

Used as progressive enhancement, `sibling-index()` offers a compact, declarative replacement for a common category of manually assigned sequence values.

Further reading: [CSS Values and Units Level 5 — `sibling-index()`](https://drafts.csswg.org/css-values-5/#funcdef-sibling-index)
