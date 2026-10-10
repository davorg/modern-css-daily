---
title: "scroll-marker-group"
date: 2026-10-10
categories: ["CSS"]
tags: ["scroll-marker-group"]
layout: single
source: "https://drafts.csswg.org/css-overflow-5/#propdef-scroll-marker-group"
---

`scroll-marker-group` is an experimental CSS property for creating a group of navigation markers associated with a scroll container. It is designed primarily for interfaces such as carousels, galleries, and paginated horizontal lists.

The property accepts three values: `none`, `before`, and `after`. The initial value, `none`, creates no marker group. `before` or `after` generates a `::scroll-marker-group` pseudo-element before or after the scroll container’s contents. Descendants can generate individual `::scroll-marker` pseudo-elements, which the browser collects into that group.

Here is a minimal carousel:

```html
<ul class="slides">
  <li>First slide</li>
  <li>Second slide</li>
  <li>Third slide</li>
</ul>
```

```css
.slides {
  display: flex;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scroll-marker-group: after;
}

.slides > li {
  flex: 0 0 100%;
  box-sizing: border-box;
  padding: 3rem;
  list-style: none;
  scroll-snap-align: start;
}

.slides::scroll-marker-group {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
}

.slides > li::scroll-marker {
  content: "";
  display: block;
  width: 0.75rem;
  height: 0.75rem;
  border-radius: 50%;
  background: #aaa;
}

.slides > li::scroll-marker:target-current {
  background: #222;
}
```

Each list item creates a marker. Activating a marker asks the browser to scroll its originating item into view, while `:target-current` identifies the marker corresponding to the current scroll target.

This is useful because carousel navigation has traditionally required JavaScript to create controls, connect them to slides, update the selected state, and respond to scrolling. Scroll markers move much of that coordination into CSS and the browser. They can therefore reduce application code and avoid marker state becoming out of sync with the actual scroll position. Because the feature builds on native scrolling and scroll snapping, it is also suitable as a progressive enhancement.

However, `scroll-marker-group` is defined in the CSS Overflow Module Level 5 Editor’s Draft and remains experimental. Support is not universal, and both implementation behavior and the specification may change. Test in your target browsers, retain usable scrolling when markers are unavailable, and do not rely on generated dots as the only way to understand or navigate important content. Keyboard behavior, focus presentation, labeling, and reduced-motion preferences also deserve explicit testing.

Further reading: [CSS Overflow Module Level 5 — `scroll-marker-group`](https://drafts.csswg.org/css-overflow-5/#propdef-scroll-marker-group)
