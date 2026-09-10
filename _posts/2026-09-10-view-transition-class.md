---
title: "view-transition-class"
date: 2026-09-10
categories: ["CSS"]
tags: ["view-transition-class"]
layout: single
source: "https://drafts.csswg.org/css-view-transitions-2/#view-transition-class-prop"
---

`view-transition-class` lets multiple named view transitions share the same styling. It assigns one or more custom identifiers to an element’s generated view-transition pseudo-elements. Those identifiers can then be matched in selectors such as `::view-transition-group(*.card)`.

This solves a practical problem with `view-transition-name`: names identify individual transitions, while classes describe categories of transitions. A unique name might connect a particular card between two states, but a class can apply the same duration or animation treatment to every card.

```css
.featured-card {
  view-transition-name: featured-card;
  view-transition-class: card;
}

::view-transition-group(*.card) {
  animation-duration: 300ms;
}
```

The example assumes that a view transition is triggered separately, through a same-document transition or a supported cross-document navigation. The `card` value is not an HTML class and is written without a leading dot in the property. The dot appears only when matching it in a view-transition pseudo-element selector.

The property’s current value syntax is:

```css
view-transition-class: none | <custom-ident>+;
```

That means an element can have no transition classes, one class, or a space-separated list:

```css
.featured-card {
  view-transition-class: card emphasized;
}
```

A transition class is useful only in conjunction with a non-`none` `view-transition-name`, because the browser must generate named view-transition pseudo-elements for the class to style.

This feature is especially useful for component systems. Components can retain distinct transition names while sharing reusable visual behavior such as timing, easing, blending, or animation definitions. It also avoids large selector lists containing every transition name.

`view-transition-class` is defined in CSS View Transitions Module Level 2, which is currently a CSS Working Group Editor’s Draft rather than a finalized Recommendation. Its details may still change. Browser support is not uniform, and support for view transitions generally does not necessarily imply support for this Level 2 property or its class-matching selector syntax. Treat it as progressive enhancement, test in your target browsers, and ensure the interface remains usable when the declaration or related selectors are ignored.

Further reading: [CSS View Transitions Module Level 2 — `view-transition-class`](https://drafts.csswg.org/css-view-transitions-2/#view-transition-class-prop)
