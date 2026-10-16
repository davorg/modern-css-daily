---
title: "inverted-colors"
date: 2026-10-16
categories: ["CSS"]
tags: ["inverted-colors"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#inverted"
---

The `inverted-colors` media feature lets a page detect whether the user agent or operating system is displaying content with inverted colors. Such modes are commonly used as an accessibility aid. They can improve text readability for some users, but they may also make photographs, illustrations, and other color-sensitive content look like photographic negatives.

The feature has two values:

- `none`: Colors are displayed normally.
- `inverted`: All pixels in the displayed area have been inverted.

Here is a minimal example:

```css
@media (inverted-colors: inverted) {
  .color-critical-image {
    filter: invert(100%);
  }
}
```

When the environment performs a final color inversion, applying an inversion to selected content first can effectively counter-invert it. This may help a photograph or diagram retain something closer to its intended appearance. Apply this selectively: counter-inverting text, controls, or an entire page could undermine the user’s chosen accessibility setting.

`inverted-colors` is useful today as a progressive enhancement. A page does not need the query to function, but where the environment exposes an inverted-color mode, authors can make focused adjustments. Besides counter-inverting certain images, a site might swap a color-dependent illustration for a simpler alternative or remove decorative effects that become distracting after inversion.

The feature is defined in Media Queries Level 5. The cited specification is an Editor’s Draft, so the feature remains part of a draft standard rather than a finalized W3C Recommendation. Browser and platform behavior should therefore be tested in the environments your users rely on; do not assume the query is available everywhere.

There are also important limits. The query reports whether displayed colors are inverted, not why the user enabled the mode or what design they would prefer. It does not provide details about a platform’s inversion algorithm, and it is distinct from other accessibility-related features such as forced colors or contrast preferences. Keep the default experience usable, place adaptations inside the media query, and verify them with real content—especially images, transparency, shadows, gradients, and embedded media.

Above all, treat `inverted-colors` as a signal for small, evidence-based corrections, not as permission to override an accessibility preference.

Further reading: [CSS Media Queries Level 5: Detecting inverted colors](https://drafts.csswg.org/mediaqueries-5/#inverted)
