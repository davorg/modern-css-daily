---
title: "margin-trim"
date: 2026-08-27
categories: ["CSS"]
tags: ["margin-trim"]
layout: single
source: "https://drafts.csswg.org/css-box-4/#margin-trim"
---

`margin-trim` lets a container remove child margins that would otherwise appear at the container’s edges. It is designed for layouts where children own their spacing but the parent should control whether that spacing remains at its boundaries.

Consider a stack of elements whose children use block margins:

```css
.stack {
  padding: 1rem;
  margin-trim: block;
}

.stack > * {
  margin-block: 1rem;
}
```

With `margin-trim: block`, the container trims the relevant block-axis margins at its block-start and block-end edges. Margins between the children still provide separation, but the first and last child do not add unwanted space next to the container’s padding.

This is especially useful in reusable components. Without `margin-trim`, a component often needs rules such as `:first-child` and `:last-child`, or selectors that assign margins only between siblings. Those approaches work, but they couple the parent to its current child structure. They can also become awkward when conditional rendering changes which element is first or last.

`margin-trim` supports a more composable spacing model: content elements can carry their normal margins, while a card, panel, or layout wrapper decides whether those margins should affect its edges. Because the example uses the logical `block` axis, the behavior also follows the document’s writing mode rather than assuming physical top and bottom edges.

The property is defined in the CSS Box Model Module Level 4 specification. That specification is a draft, so `margin-trim` should be treated as an evolving, experimental feature rather than an established cross-browser baseline.

Before using it in production, check current browser compatibility and test the layouts you depend on. Browsers that do not recognize the declaration will ignore it, leaving the children’s original edge margins in place. That may be an acceptable progressive-enhancement fallback, but it can also create extra spacing. If consistent spacing is essential, retain an established fallback—such as sibling selectors, explicit first/last-child handling, or `gap` where the layout model makes it appropriate—and apply `margin-trim` as an enhancement.

Also test interactions with margin collapsing, nested containers, fragmentation, and different layout modes. The specification defines detailed trimming behavior, and simplified mental models may not cover every formatting context.

Further reading: [CSS Box Model Module Level 4: Margin Trimming](https://drafts.csswg.org/css-box-4/#margin-trim)
