---
title: "translate"
date: 2026-08-16
categories: ["CSS"]
tags: ["translate"]
layout: single
source: "https://drafts.csswg.org/css-transforms-2/#propdef-translate"
---

The CSS `translate` property moves a transformable element without requiring a `transform` function. It is one of the individual transform properties defined by **CSS Transforms Module Level 2**, alongside `rotate` and `scale`.

The specification is currently published as an Editor’s Draft, so it is part of an evolving CSS standard rather than a finalized Recommendation. Avoid assuming support from the specification’s status alone; check current compatibility data for the browsers you target.

A minimal example:

```css
.card {
  translate: 0 0;
  transition: translate 150ms ease;
}

.card:hover {
  translate: 0 -0.5rem;
}
```

The property accepts one, two, or three components:

- One value specifies the horizontal translation.
- Two values specify horizontal and vertical translation.
- Three values specify horizontal, vertical, and depth translation.

The first two components accept lengths or percentages. The third component accepts a length, not a percentage. The keyword `none` represents no translation.

Percentages are resolved relative to the element’s reference box. For example, this common centering pattern offsets an element by half of its own reference-box dimensions:

```css
.dialog {
  position: fixed;
  left: 50%;
  top: 50%;
  translate: -50% -50%;
}
```

The main benefit is separation of concerns. With the traditional `transform` property, adding a translation can accidentally replace an existing rotation or scale:

```css
/* Replaces the entire transform value */
.item {
  transform: translateY(-0.5rem);
}
```

Using `translate`, a component can adjust position while another rule independently controls `rotate`, `scale`, or `transform`. It is also directly animatable, making it convenient for hover effects, transitions, and scripted motion.

There are some caveats. Individual transform properties are applied in a defined order: `translate`, then `rotate`, then `scale`, followed by the functions in `transform`. That fixed ordering may produce a different result from a manually ordered `transform` function list. Translation also changes an element’s rendered position without changing normal document flow, so surrounding layout does not move to accommodate it. Finally, test fallbacks where support in your target environment is uncertain, and consider reduced-motion preferences when animating the property.

Further reading: [CSS Transforms Module Level 2 — `translate`](https://drafts.csswg.org/css-transforms-2/#propdef-translate)
