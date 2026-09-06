---
title: "text-wrap-mode"
date: 2026-09-06
categories: ["CSS"]
tags: ["text-wrap-mode"]
layout: single
source: "https://drafts.csswg.org/css-text-4/#text-wrap-mode-property"
---

`text-wrap-mode` controls whether text may wrap at soft wrap opportunities during inline layout. It accepts two values:

- `wrap`: wrapping is allowed when needed.
- `nowrap`: soft wrapping is suppressed.

Forced line breaks, such as explicit line breaks in preserved content, are still honored. The property is inherited, so applying it to a container can affect text throughout its descendants.

`text-wrap-mode` is defined in the CSS Text Module Level 4 specification. That specification is still a CSS Working Group draft, not a finalized Recommendation, so details and implementations may continue to evolve.

A minimal example is:

```css
.navigation-label {
  text-wrap-mode: nowrap;
}
```

This keeps each navigation label on one line unless the content contains a forced break.

The main advantage over broader whitespace controls is precision. Historically, developers have often used `white-space: nowrap`, but `white-space` also controls how spaces and other whitespace are collapsed or preserved. `text-wrap-mode` lets a component express only its wrapping requirement without intentionally changing whitespace processing.

That separation is useful in design systems and reusable components. A badge, tab, button label, or data-table cell may need to stay on one line while inheriting the surrounding document’s whitespace behavior. Conversely, a component can explicitly restore wrapping with:

```css
.article-content {
  text-wrap-mode: wrap;
}
```

There are important caveats. Browser support may not be uniform, so check current compatibility data and test the browsers required by your project. Where a fallback is appropriate, place an established declaration first:

```css
.navigation-label {
  white-space: nowrap;
  text-wrap-mode: nowrap;
}
```

Browsers that do not recognize `text-wrap-mode` will ignore it and retain the fallback. Be aware that the fallback also establishes `white-space` behavior, so verify that its whitespace-collapsing semantics match your needs.

Suppressing wrapping can also cause overflow. `text-wrap-mode` does not decide whether overflowing content is clipped, scrolled, or otherwise presented; handle that separately according to the component’s design and accessibility requirements. Because the property inherits, avoid setting `nowrap` too high in the document tree unless all affected descendants should share it.

Further reading: [CSS Text Module Level 4 — `text-wrap-mode`](https://drafts.csswg.org/css-text-4/#text-wrap-mode-property)
