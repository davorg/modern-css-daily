---
title: "appearance"
date: 2026-10-27
categories: ["CSS"]
tags: ["appearance"]
layout: single
source: "https://drafts.csswg.org/css-ui-4/#appearance-switching"
---

The CSS `appearance` property controls whether an element uses the browser or operating system’s native widget styling. It is especially relevant to form controls such as buttons, checkboxes, and `<select>` elements, whose default rendering can vary between platforms.

`appearance` is defined in CSS Basic User Interface Module Level 4. That specification is an evolving CSS Working Group draft rather than a finalized W3C Recommendation, so details may still change.

The two broadly useful values are:

- `auto`, which allows the user agent to use the element’s native appearance where applicable.
- `none`, which suppresses that native appearance so the element can be rendered using ordinary CSS.

For example, a semantic button can keep its built-in behavior while receiving a fully specified visual treatment:

```html
<button type="button">Save changes</button>
```

```css
button {
  appearance: none;
  padding: 0.5rem 0.8rem;
  border: 2px solid currentColor;
  border-radius: 0.4rem;
  background: Canvas;
  color: CanvasText;
  font: inherit;
}

button:focus-visible {
  outline: 3px solid Highlight;
  outline-offset: 2px;
}
```

This is useful when native widget styling prevents consistent design across browsers and operating systems. Unlike replacing a button with a generic `<div>`, applying `appearance: none` preserves the button’s HTML semantics, keyboard behavior, form integration, and accessibility-tree role. The property changes presentation, not meaning.

The specification also defines `base-select`, a specialized value for `<select>` elements and their picker, as well as compatibility values for legacy behavior. Support for newer parts of the specification may differ between engines, so test them in the browsers relevant to your project.

There are important caveats. Removing native styling also removes many useful visual affordances. A checkbox may no longer look checked, a button may no longer look clickable, and focus or disabled states may become unclear unless you style them explicitly. Test hover, focus, checked, disabled, invalid, high-contrast, and forced-colors states where relevant.

Native appearance also varies intentionally with the user’s platform and settings. Replacing it can reduce familiarity or conflict with accessibility preferences. Use `appearance: none` when custom presentation provides a real benefit, not merely to erase defaults. The property does not turn a non-form element into a functional control.

Further reading: [CSS Basic User Interface Module Level 4 — Switching appearance](https://drafts.csswg.org/css-ui-4/#appearance-switching)
