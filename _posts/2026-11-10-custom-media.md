---
title: "@custom-media"
date: 2026-11-10
categories: ["CSS"]
tags: ["@custom-media"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#custom-mq"
---

CSS often repeats the same media-query condition across many components. `@custom-media` lets you assign a descriptive, author-defined name to a media query and reference that name from `@media` rules.

The feature is defined in **CSS Media Queries Level 5**, which is currently an Editor’s Draft rather than a finalized W3C Recommendation. Its syntax and behavior may still change, so production use requires appropriate compatibility planning.

A custom media query is declared with the `@custom-media` at-rule. Its name must be a dashed identifier, such as `--compact`:

```css
@custom-media --compact (max-width: 48rem);

@media (--compact) {
  .toolbar {
    gap: 0.5rem;
  }
}
```

Here, `--compact` represents `(max-width: 48rem)`. The named query can then be reused anywhere the same responsive condition is needed:

```css
@media (--compact) {
  .sidebar {
    display: none;
  }
}
```

This is useful because breakpoints and capability checks often act like design tokens. Naming them makes their purpose clearer: `--compact` communicates intent better than repeating a raw width everywhere. It also centralizes maintenance. If a project’s compact-layout breakpoint changes, authors can update one definition instead of searching through multiple stylesheets.

Custom media queries can represent more than viewport widths. They can name any valid media-query list, allowing teams to give consistent vocabulary to conditions involving input capabilities, display characteristics, user preferences, or combinations of those conditions.

The main caveat is native browser support. Because `@custom-media` remains a draft feature, do not assume that every browser used by your audience will evaluate it. Check current compatibility information rather than relying on old version tables or support percentages.

Today, the feature is commonly practical through build-time CSS processing. A suitable tool can replace named queries with their underlying media conditions, producing conventional `@media` rules for browsers. Verify that the processor follows the current specification, include the relevant transformation in production builds, and inspect the generated CSS. Without native support or preprocessing, styles placed only behind a custom media query may not be applied as intended.

`@custom-media` is therefore best viewed as a small but valuable maintainability feature: it gives repeated media conditions meaningful names while keeping responsive decisions consistent across a codebase.

Further reading: [CSS Media Queries Level 5 — Custom Media Queries](https://drafts.csswg.org/mediaqueries-5/#custom-mq)
