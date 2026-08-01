---
title: "accent-color-experimental"
date: 2026-05-31
categories: ["CSS"]
tags: [accent-color-experimental]
layout: single
---

> **Correction — 1 August 2026:** The original version of this article described `accent-color-experimental` as a CSS feature. That was incorrect, so the erroneous article has been replaced.

CSS defines the [`accent-color`](https://www.w3.org/TR/css-ui-4/#widget-accent) property; it does not define a separate `accent-color-experimental` property, function, selector, or media query.

The valid syntax is `accent-color: auto` or `accent-color: <color>`. It lets a browser use the chosen colour for accented parts of applicable user-interface controls, such as checkboxes and radio buttons:

```css
:root {
  accent-color: rebeccapurple;
}
```

The browser remains responsible for rendering the control and maintaining legibility. It may adjust the supplied colour or related foreground colours to preserve contrast. Authors should therefore not assume exact cross-platform rendering.

Further reading: [CSS Basic User Interface Module Level 4](https://www.w3.org/TR/css-ui-4/#widget-accent).
