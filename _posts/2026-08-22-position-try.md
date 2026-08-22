---
title: "@position-try"
date: 2026-08-22
categories: ["CSS"]
tags: ["@position-try"]
layout: single
source: "https://drafts.csswg.org/css-anchor-position-1/#at-ruledef-position-try"
---

`@position-try` defines a named fallback placement for an anchor-positioned element. When the element’s preferred position would overflow its containing block, the browser can try one or more alternative configurations.

The feature is part of the CSS Anchor Positioning Module Level 1. The linked document is an Editor’s Draft, so the syntax and behavior may still change as the specification develops.

Here is a minimal example:

```css
.trigger {
  anchor-name: --trigger;
}

.tooltip {
  position: absolute;
  position-anchor: --trigger;

  /* Preferred placement */
  position-area: top;

  /* Named fallback */
  position-try-fallbacks: --below;
}

@position-try --below {
  position-area: bottom;
}
```

The `.trigger` element establishes an anchor named `--trigger`. The absolutely positioned `.tooltip` selects that anchor and asks to appear above it. If that placement does not fit, `position-try-fallbacks` tells the browser to try the `--below` option defined by `@position-try`.

A `@position-try` name is a `<dashed-ident>`, such as `--below`. Its declarations describe an alternative positioning configuration. Multiple named options can be listed in `position-try-fallbacks`, allowing the browser to test them in order.

This is useful for tooltips, menus, teaching overlays, callouts, and similar interface elements. Traditionally, placing these components requires JavaScript to measure both the anchor and the positioned element, detect viewport or container edges, and switch classes or inline styles. Anchor positioning and position tries move much of that layout work into CSS. Named `@position-try` rules also make fallback strategies reusable and easier to understand than duplicated positioning declarations.

There are important caveats. This remains draft technology, and implementation availability is not uniform across browsers. Check current compatibility information and test the exact behavior you depend on. For production interfaces, provide a reasonable non-anchored or fixed-placement fallback, and consider JavaScript when consistent placement is essential.

Position tries are also not a general-purpose layout or collision-detection system. They select among declared alternatives according to the specification’s overflow and fitting rules; authors must still define useful fallback positions. The positioned element must also be connected to an anchor—`@position-try` does not create that relationship by itself.

Further reading: [CSS Anchor Positioning Level 1 — `@position-try`](https://drafts.csswg.org/css-anchor-position-1/#at-ruledef-position-try)
