---
title: "prefers-reduced-transparency"
date: 2026-09-04
categories: ["CSS"]
tags: ["prefers-reduced-transparency"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#prefers-reduced-transparency"
---

`prefers-reduced-transparency` is a CSS media feature for detecting whether a user has requested an interface with fewer transparent or translucent effects. It is defined in Media Queries Level 5, which is currently a CSS Working Group draft rather than a finalized Recommendation.

The feature has two values:

- `reduce`: the user has expressed a preference for reduced transparency.
- `no-preference`: the user has not expressed such a preference.

A minimal use looks like this:

```css
.card {
  background: rgb(255 255 255 / 70%);
}

@media (prefers-reduced-transparency: reduce) {
  .card {
    background: #fff;
  }
}
```

In this example, the default card background is translucent. When the browser reports a preference for reduced transparency, the background becomes fully opaque.

Transparency can make interfaces feel layered and visually rich, but it can also make content harder to distinguish from whatever appears behind it. Backdrop effects, translucent navigation bars, overlays, and semi-transparent panels may reduce clarity or create distracting visual interactions. Respecting this preference can therefore improve legibility and make page structure easier to understand.

The feature is useful as a progressive enhancement today. You can keep an accessible, readable default design and use the query to remove transparency where the user’s browser and operating environment expose the preference. It is generally better to replace translucent surfaces with suitable opaque colors than simply to remove them without considering contrast and hierarchy.

There are important caveats. Media queries report what the user agent makes available; they do not reveal why a preference was chosen. Avoid making assumptions about a user’s condition or needs. Support also varies across browsers and operating systems, so do not rely on this query as the only way to make text readable or controls distinguishable. Browsers that do not recognize the feature will ignore the media-query block and retain the base styles.

This preference is also distinct from `prefers-reduced-motion` and other user-preference media features. A user may request reduced transparency without requesting fewer animations, or vice versa. Treat each preference independently and test the resulting combinations.

Further reading: [CSS Media Queries Level 5 — `prefers-reduced-transparency`](https://drafts.csswg.org/mediaqueries-5/#prefers-reduced-transparency)
