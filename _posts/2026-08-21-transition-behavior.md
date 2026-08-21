---
title: "transition-behavior"
date: 2026-08-21
categories: ["CSS"]
tags: ["transition-behavior"]
layout: single
source: "https://drafts.csswg.org/css-transitions-2/#transition-behavior-property"
---

`transition-behavior` controls whether CSS transitions can start for properties with a **discrete animation type**. It is defined in the CSS Transitions Level 2 Editor’s Draft, so it is a draft feature whose details may still evolve.

By default, `transition-behavior` is `normal`: transitions are not started for discrete properties. Setting it to `allow-discrete` permits them. This does not make discrete values gradually interpolable; they still switch between values at a defined point during the transition.

A common use case is coordinating an opacity fade with `display: none`:

```css
.notice {
  display: block;
  opacity: 1;
  transition:
    opacity 200ms ease,
    display 200ms allow-discrete;
}

.notice.is-hidden {
  display: none;
  opacity: 0;
}

@starting-style {
  .notice {
    opacity: 0;
  }
}
```

Adding `is-hidden` lets the notice fade out while the discrete `display` transition participates in the same transition sequence. Removing the class can fade it back in. The `@starting-style` rule supplies an initial opacity for cases where the element did not previously have a rendered before-change style.

The feature is also available as a longhand:

```css
.notice {
  transition-property: opacity, display;
  transition-duration: 200ms;
  transition-behavior: normal, allow-discrete;
}
```

This is useful because UI elements often combine interpolable properties—such as `opacity` or `transform`—with discrete state changes. Without discrete transitions, developers may need JavaScript, timers, animation events, or extra classes to delay the discrete change until a visual transition finishes. `transition-behavior` makes that coordination declarative and keeps timing in CSS.

There are important caveats. A discrete property does not become smoothly animated merely because `allow-discrete` is present. Its value still changes discretely according to that property’s animation rules. Entry transitions may also require `@starting-style`, depending on whether the element has a previous rendered style.

Browser support should be checked for the environments you target; do not assume that support for ordinary CSS transitions implies support for `transition-behavior` or `@starting-style`. Consider using `@supports (transition-behavior: allow-discrete)` when layering this behavior over a fallback. Also prefer explicit transition-property lists: applying `allow-discrete` broadly may cause unrelated state changes to participate in transitions.

Further reading: [CSS Transitions Level 2 — `transition-behavior`](https://drafts.csswg.org/css-transitions-2/#transition-behavior-property)
