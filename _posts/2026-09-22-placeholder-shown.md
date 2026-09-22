---
title: ":placeholder-shown"
date: 2026-09-22
categories: ["CSS"]
tags: [":placeholder-shown"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#placeholder"
---

`:placeholder-shown` is a CSS pseudo-class that matches an input control while it is displaying placeholder text. The placeholder may come from an attribute, an element, or another mechanism provided by the user agent.

It is defined in the Selectors Level 4 specification. That specification remains a draft, so the feature is standards-track but its definition may still be refined.

A minimal example uses an HTML `placeholder` attribute:

```html
<label for="email">Email address</label>
<input
  id="email"
  type="email"
  placeholder="name@example.com"
>

<style>
  input {
    border: 2px solid #2673d9;
  }

  input:placeholder-shown {
    border-color: #777;
    background: #f5f5f5;
  }
</style>
```

Here, the second rule applies while the input is showing `name@example.com`. When the user enters a value and the placeholder is no longer displayed, the rule stops matching. If the value is cleared and the placeholder appears again, the input can match again.

This is useful because it exposes a common control state directly to CSS. Developers can provide a visual distinction between a field showing a hint and one containing a value, implement parts of a floating-label interface, or adjust spacing and decoration without adding JavaScript event listeners or state classes.

There are important limits. `:placeholder-shown` is not a general-purpose test for an empty value. A control without placeholder text will not match merely because it is empty. Likewise, the pseudo-class describes whether placeholder text is being shown; it does not indicate whether the field is valid, required, visited, or modified by the user.

The selector matches the input control itself, so declarations such as borders, backgrounds, or layout properties affect that control. Do not treat placeholder text as a replacement for an accessible label: placeholders can disappear during input and may not provide enough persistent context. Use a proper `<label>` when the control needs a name.

Implementation details and placeholder behavior may differ across user agents and control types. Check current compatibility information and test the specific controls and browsers required by your project rather than assuming uniform behavior.

Further reading: [Selectors Level 4 — The Placeholder-shown Pseudo-class](https://drafts.csswg.org/selectors-4/#placeholder)
