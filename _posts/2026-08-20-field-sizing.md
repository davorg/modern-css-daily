---
title: "field-sizing"
date: 2026-08-20
categories: ["CSS"]
tags: ["field-sizing"]
layout: single
source: "https://drafts.csswg.org/css-ui-4/#field-sizing"
---

`field-sizing` controls whether certain form controls use their conventional fixed preferred size or size themselves from their contents. It is especially useful for controls such as `<input>`, `<textarea>`, and `<select>`, whose default dimensions often do not reflect the value they contain.

The property accepts two values:

- `fixed`, the initial value, preserves the control’s normal default sizing behavior.
- `content` removes that default preferred size, allowing the control’s content to influence its dimensions.

A minimal example looks like this:

```html
<label>
  Notes
  <textarea class="content-sized">Short note</textarea>
</label>

<style>
  .content-sized {
    field-sizing: content;
    min-inline-size: 12ch;
    max-inline-size: 40ch;
  }
</style>
```

Here, the `<textarea>` can size according to its content instead of starting with its usual fixed preferred dimensions. The minimum and maximum inline sizes keep it usable when the content is unusually short or long. Other sizing properties and layout constraints still apply, so `field-sizing: content` does not mean “grow without limits.”

This is valuable because content-aware form controls have traditionally required JavaScript. Auto-growing text areas, compact selects, and inputs that expand with their values often involve measuring text, listening for input events, and updating dimensions manually. When the desired behavior matches CSS’s content-based sizing model, `field-sizing` can replace that code with one declaration. It also lets the browser participate directly in sizing as values, placeholder text, or available layout space change.

`field-sizing` is defined in CSS Basic User Interface Module Level 4. That specification is still a draft rather than a finalized standard, and implementation availability may differ between browsers. Avoid assuming that every user has support, and test the behavior required by your design.

Because unsupported CSS declarations are ignored, the feature can usually be introduced as a progressive enhancement. An explicit feature query is also available when different fallback styling is needed:

```css
textarea {
  min-inline-size: 12ch;
  max-inline-size: 40ch;
}

@supports (field-sizing: content) {
  textarea {
    field-sizing: content;
  }
}
```

Keep a usable default size, set sensible minimum or maximum constraints, and verify behavior with long content, empty values, placeholders, and the form controls you actually use.

Further reading: [CSS Basic User Interface Module Level 4 — `field-sizing`](https://drafts.csswg.org/css-ui-4/#field-sizing)
