---
title: "caret-color"
date: 2026-10-06
categories: ["CSS"]
tags: ["caret-color"]
layout: single
source: "https://drafts.csswg.org/css-ui-4/#caret-color"
---

The CSS `caret-color` property controls the color of the text insertion caret—the blinking marker that shows where typed text will appear in an editable element.

It is defined in the CSS Basic User Interface Module Level 4 specification, currently published as an Editor’s Draft. That means it is part of ongoing standards work rather than a finalized W3C Recommendation, so details may still change. The property’s current syntax accepts either `auto` or a CSS `<color>` value:

```css
input,
textarea {
  caret-color: #d12f5a;
}
```

Because `caret-color` is inherited, it can also be applied to a container to affect editable descendants:

```css
.form {
  color: white;
  background: #20232a;
  caret-color: #7ee787;
}
```

The initial value is `auto`. With `auto`, the user agent chooses the caret color. The specification recommends using `currentColor`, while allowing the browser to adjust the result when necessary to keep the caret visible against its surroundings.

This feature is useful for forms, search boxes, rich-text editors, and elements using `contenteditable`. A custom caret can reinforce a visual theme and, more importantly, prevent an insertion point from becoming difficult to see in dark interfaces or components with unusual foreground and background colors.

Use it with care. The caret is a functional indicator, not merely decoration, so its color should have strong contrast with the field’s background. Avoid making it transparent unless hiding the insertion caret is genuinely intended. Also remember that `caret-color` changes the insertion caret only; it does not change selected-text colors, focus indicators, borders, placeholders, or other editing UI.

Browsers and user agents may make visibility-related adjustments, and accessibility modes or user settings can affect the final presentation. As with any interface detail, test the result in the browsers and environments your project supports rather than assuming identical rendering everywhere. Keep a visible focus style as well: a colorful caret is not a substitute for indicating which control has keyboard focus.

Further reading: [CSS Basic User Interface Module Level 4 — `caret-color`](https://drafts.csswg.org/css-ui-4/#caret-color)
