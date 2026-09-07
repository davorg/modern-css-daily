---
title: "prefers-contrast"
date: 2026-09-07
categories: ["CSS"]
tags: ["prefers-contrast"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#prefers-contrast"
---

`prefers-contrast` is a CSS media feature that detects whether a user has asked the system to adjust the contrast between adjacent colors. It allows a site to respond to preferences exposed by the operating system or user agent without requiring JavaScript.

The feature is defined in CSS Media Queries Level 5, an evolving CSSWG draft rather than a finalized Recommendation. Its syntax and behavior could therefore still change.

The feature accepts four values:

- `no-preference`: the user agent has no contrast preference to report.
- `more`: the user prefers more contrast than the interface’s default.
- `less`: the user prefers less contrast than the default.
- `custom`: the user prefers a particular color palette whose contrast is not represented by `more` or `less`.

A minimal use looks like this:

```css
.notice {
  border: 1px solid #777;
}

@media (prefers-contrast: more) {
  .notice {
    border-width: 3px;
    border-color: currentColor;
  }
}
```

This example strengthens the notice boundary when the user requests more contrast. In a real design, you might also make focus indicators more prominent, reduce reliance on subtle color differences, or increase separation between controls and their backgrounds.

`prefers-contrast` is useful today as a progressive enhancement. It can help an interface respect user preferences automatically while keeping the default design available everywhere. Because it participates in the normal cascade, contrast-specific styles can be small overrides rather than a separate theme.

There are important caveats. Implementation and integration with system settings can vary, so check current compatibility data and test on the browsers and operating systems you support. Do not assume that every device exposes a contrast preference, or that `no-preference` means the user actively prefers your default styling.

The values are also preferences, not guaranteed contrast ratios. A `more` query does not prove that the resulting design meets any particular accessibility requirement. Start with an accessible default, then use the media feature to improve it further.

Finally, treat `custom` as distinct from `more`. It may reflect a user-selected palette, including situations involving forced colors. If your interface needs to account for forced-color rendering, test that behavior separately rather than assuming all custom palettes simply require higher contrast.

**Further reading:** [CSS Media Queries Level 5: `prefers-contrast`](https://drafts.csswg.org/mediaqueries-5/#prefers-contrast)
