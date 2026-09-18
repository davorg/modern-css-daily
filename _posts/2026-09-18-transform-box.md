---
title: "transform-box"
date: 2026-09-18
categories: ["CSS"]
tags: ["transform-box"]
layout: single
source: "https://drafts.csswg.org/css-transforms/#transform-box-property"
---

`transform-box` controls the reference box used by an element’s `transform` and `transform-origin`. In other words, it determines which bounds CSS treats as the coordinate system for operations such as rotation, scaling, and translation.

The property is defined in CSS Transforms Module Level 1. The linked specification is the CSS Working Group’s Editor’s Draft, so it represents current standards work rather than a permanently frozen document.

Its syntax accepts five keywords:

- `content-box` — use the CSS content box.
- `border-box` — use the CSS border box.
- `fill-box` — use an SVG element’s object bounding box.
- `stroke-box` — use an SVG element’s stroke bounding box.
- `view-box` — use the nearest SVG viewport, accounting for its `viewBox` when present.

The initial value is `view-box`. Some values map to equivalent CSS or SVG boxes when the requested kind of box does not apply to the element.

A common use case is rotating an individual SVG shape around its own center rather than around the entire SVG viewport:

```html
<svg viewBox="0 0 100 100" width="120" height="120">
  <rect class="marker" x="20" y="35" width="60" height="30" />
</svg>

<style>
  .marker {
    fill: tomato;
    transform-box: fill-box;
    transform-origin: center;
    transform: rotate(30deg);
  }
</style>
```

Here, `fill-box` makes the rectangle’s filled bounds the reference box. Consequently, `transform-origin: center` identifies the center of that rectangle. Without an appropriate reference box, the same origin can be resolved relative to the SVG viewport, producing a visibly different rotation.

This is useful today because SVG icons, charts, diagrams, and interface controls often contain several independently transformed shapes. `transform-box` lets styles state explicitly whether a transform should relate to the shape itself, its stroke, or the surrounding viewport. It can also clarify transformations on ordinary CSS boxes by choosing between the content and border bounds.

There are caveats. The distinctions between `fill-box`, `stroke-box`, and `view-box` matter primarily for SVG, while the specification defines mappings for elements that have only a CSS layout box or only an SVG bounding box. SVG bounding boxes can also change when geometry or stroke properties change, which may alter the visual pivot. Finally, support should be tested against the browsers and element types required by your project rather than assumed; if the property is unsupported, its declaration will be ignored and the default transform reference behavior will remain.

Further reading: [CSS Transforms Module Level 1 — `transform-box`](https://drafts.csswg.org/css-transforms/#transform-box-property)
