---
title: "animation-range"
date: 2026-11-13
categories: ["CSS"]
tags: ["animation-range"]
layout: single
source: "https://drafts.csswg.org/scroll-animations-1/#propdef-animation-range"
---

`animation-range` controls which portion of an animation’s timeline is used to run the animation. It is especially useful with scroll-driven animations: instead of mapping an animation across an entire scroll or view progress timeline, you can make it begin and end at meaningful points, such as while an element enters the viewport.

The property is a shorthand for `animation-range-start` and `animation-range-end`. Its values can identify named timeline ranges, optionally with percentages or lengths that offset positions within those ranges. For view progress timelines, named ranges include `entry`, `exit`, `cover`, and `contain`.

Here is a minimal example:

```css
@keyframes reveal {
  from {
    opacity: 0;
    transform: translateY(2rem);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.card {
  animation: reveal linear both;
  animation-timeline: view();
  animation-range: entry 0% cover 40%;
}
```

`animation-timeline: view()` creates an anonymous view progress timeline for each `.card`. The `animation-range` declaration attaches the start of the animation to `0%` of the `entry` range—the point at which the element begins entering—and its end to `40%` of the `cover` range.

This is useful because scroll-linked effects rarely need to occupy an entire timeline. A reveal may need to finish shortly after an element appears, while another effect might run only during its exit. Expressing those boundaries declaratively avoids JavaScript scroll handlers, geometry calculations, and repeated updates on every scroll event. It also keeps the timing relationship next to the animation itself in CSS.

`animation-range` is defined in the CSS Scroll-driven Animations Level 1 specification. That document is an Editor’s Draft, so the feature remains a work in progress rather than a finalized web standard.

Browser implementation is not uniform, and support for parsing the property does not necessarily prove that every timeline type or named range behaves identically. Treat it as a progressive enhancement, test in your target browsers, and provide a sensible static or time-based fallback. Feature queries can help:

```css
@supports (animation-timeline: view()) and
          (animation-range: entry 0% cover 40%) {
  /* Apply the scroll-driven animation here. */
}
```

Also consider users who request reduced motion, particularly when applying large transforms or effects across many elements.

Further reading: [CSS Scroll-driven Animations Level 1 — `animation-range`](https://drafts.csswg.org/scroll-animations-1/#propdef-animation-range)
