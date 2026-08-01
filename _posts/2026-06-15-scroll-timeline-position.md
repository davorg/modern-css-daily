---
title: "scroll-timeline-position"
date: 2026-06-15
categories: ["CSS"]
tags: [scroll-timeline-position]
layout: single
---

> **Correction — 1 August 2026:** The original version of this article described `scroll-timeline-position` as a CSS feature. That was incorrect, so the erroneous article has been replaced.

The current Scroll-driven Animations specification defines `scroll-timeline`, `scroll-timeline-name`, and `scroll-timeline-axis`. It does not define a `scroll-timeline-position` property or function.

A named scroll progress timeline can be declared on a scroll container and attached to an animation like this:

```css
.scroller {
  scroll-timeline: --page-scroll block;
}

.progress {
  animation: grow linear both;
  animation-timeline: --page-scroll;
}
```

Use `animation-range` and its longhands to restrict the part of a scroll-driven timeline used by an animation. Time-based `animation-delay` does not apply to scroll-driven animations.

Further reading: [Scroll-driven Animations Module Level 1](https://drafts.csswg.org/scroll-animations-1/).
