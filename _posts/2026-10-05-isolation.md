---
title: "isolation"
date: 2026-10-05
categories: ["CSS"]
tags: ["isolation"]
layout: single
source: "https://drafts.csswg.org/compositing-1/#isolation"
---

The CSS `isolation` property controls whether an element must create a new stacking context. Its primary purpose is to isolate a group of elements during compositing, preventing descendants that use blending from blending with content behind the group.

`isolation` is defined in CSS Compositing and Blending Level 1. The linked specification is the CSS Working Group’s Editor’s Draft on the W3C standards track; it should be treated as the current technical source rather than as a browser-release timeline.

The property accepts two values:

- `auto` — the element creates a stacking context only when another CSS rule requires one.
- `isolate` — the element must create a stacking context.

A small example shows its most common use:

```css
.card {
  isolation: isolate;
}

.card__image {
  mix-blend-mode: multiply;
}
```

With this CSS, `.card__image` can blend with content inside `.card`, such as its background, but not with content behind the card. Without `isolation: isolate`, the image’s blending may involve a backdrop outside the card, depending on the surrounding stacking contexts.

This is useful for reusable components. A component using `mix-blend-mode` should not usually change appearance according to whatever page content happens to sit behind it. Isolating the component gives its compositing behavior a predictable boundary.

Creating a stacking context can also help when implementing layered component effects. Positioned children, pseudo-elements, and negative `z-index` values can be kept within the component’s stacking context rather than interacting unexpectedly with layers outside it. This makes `isolation: isolate` a focused alternative to triggering a stacking context through unrelated visual properties.

There are several caveats. Isolation does not clip descendants, provide layout containment, or prevent overflow; use the appropriate properties for those jobs. It also does not make an element blend by itself—blending still comes from properties such as `mix-blend-mode`. Finally, because a new stacking context changes how descendants participate in `z-index` ordering, adding isolation can alter existing layering behavior.

Support should be checked against current compatibility data for the browsers relevant to a project, rather than relying on historical version claims or fixed support percentages. Visual compositing can also vary with the surrounding design, so test the complete component against realistic backgrounds.

Further reading: [CSS Compositing and Blending Level 1 — Isolation](https://drafts.csswg.org/compositing-1/#isolation)
