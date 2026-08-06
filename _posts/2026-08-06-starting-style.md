---
title: "@starting-style"
date: 2026-08-06
categories: ["CSS"]
tags: ["@starting-style"]
layout: single
source: "https://drafts.csswg.org/css-transitions-2/#at-ruledef-starting-style"
---

`@starting-style` lets you define the styles from which an element should transition when it has no previous rendered style. Normally, CSS transitions compare an element’s old computed style with its new one. A newly inserted element—or one becoming rendered after not being rendered—may not have that “before-change style,” so its entry transition would not run.

The at-rule supplies that missing starting point:

```css
.notice {
  opacity: 1;
  transform: translateY(0);
  transition:
    opacity 250ms ease,
    transform 250ms ease;
}

@starting-style {
  .notice {
    opacity: 0;
    transform: translateY(0.5rem);
  }
}
```

When a matching `.notice` first becomes rendered, it can transition from the values inside `@starting-style` to its regular values. For example, it will fade in and move upward when inserted into the document.

`@starting-style` is a grouping rule: it contains ordinary style rules whose declarations participate in calculating an element’s starting style. In this standalone form, cascade order still matters. Here, the `@starting-style` block follows the regular rule so that declarations with equal specificity provide the intended starting values.

The feature is useful because entry effects can now use the transition model rather than requiring a separate `@keyframes` animation or JavaScript that first applies one class and then removes it on a later frame. It works with existing transition controls such as `transition-duration`, `transition-delay`, and timing functions. It is especially relevant to interfaces that insert content dynamically or reveal previously unrendered UI.

There are important limits. A starting style is used only when an element lacks a before-change style for the relevant style change event; it does not redefine the starting point of every later transition. The properties must also be transitionable, and transitions still need to be declared normally. Cases involving discrete properties, such as `display`, may require other CSS Transitions Level 2 features and should not be assumed to work from `@starting-style` alone.

`@starting-style` is defined in CSS Transitions Level 2, currently a CSS Working Group Editor’s Draft rather than a finalized Recommendation. Browser support is not universal, so check current compatibility information and test the exact interaction you need. In browsers that do not recognize the at-rule, the regular final styles still apply, but the entry transition will not use the supplied starting style.

Further reading: [CSS Transitions Level 2 — `@starting-style`](https://drafts.csswg.org/css-transitions-2/#at-ruledef-starting-style)
