---
title: "has() selector"
date: 2026-02-05
categories: ["CSS"]
tags: [has() selector]
layout: single
---

The `:has()` pseudo-class is a powerful CSS feature introduced as part of the CSS Selectors Level 4 specification. Although its arrival has been anticipated for years, it began gaining practical traction in the development community with improved support across modern browsers from 2020 onwards. This pseudo-class has significantly expanded the capabilities of CSS, offering a new level of interactivity and styling dynamism without needing JavaScript for parent-level selection.

The `:has()` pseudo-class allows developers to select elements that contain certain descendant elements. In simpler terms, it enables the styling of a parent element based on the condition that it contains a specific child. This is a striking advancement because traditional CSS does not allow selecting a parent element based on its children, something that has been frequently requested by web developers.

For example, suppose you're working with a form and you want to change the styling of a `fieldset` if it contains a `legend`. With `:has()`, you can write the following code:

```css
fieldset:has(> legend) {
  border-color: blue;
  background-color: #f0f0f0;
}
```

In this scenario, any `fieldset` with a direct `legend` child will have a different border and background color, allowing visual distinction immediately through CSS.

The `:has()` pseudo-class is particularly useful in today's web environments for several reasons. It can simplify complex interactions and styling rules that previously required JavaScript workarounds. For example, it can be used to apply styles to menu items that have sub-menus, dynamically alter the layout of lists if images are present, or highlight input fields that contain error indicators. This capability enhances performance and efficiency by reducing the amount of JavaScript needed for style-related DOM manipulation.

However, like any advanced CSS feature, `:has()` comes with caveats, primarily regarding browser support. While most modern browsers like Chrome, Edge, and Safari have integrated support, it’s essential to keep an eye on compatibility issues, especially with older versions or less common browsers like Internet Explorer, which do not support it. Developers should check browser compatibility tables and consider graceful degradation or polyfills if older browser support is necessary.

In summary, the advent of the `:has()` pseudo-class has enriched CSS, providing a more expressive and powerful toolkit for web developers. It facilitates enhanced interactivity and cleaner code but should be used thoughtfully, considering browser support and the need for consistent user experiences across different devices.
