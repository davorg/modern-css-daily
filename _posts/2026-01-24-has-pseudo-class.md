---
title: "has() pseudo-class"
date: 2026-01-24
categories: ["CSS"]
tags: [has() pseudo-class]
layout: single
---

The `:has()` pseudo-class is one of the more exciting recent additions to the CSS toolkit, introduced as part of the CSS Selectors Level 4 specification. Although its arrival was highly anticipated for years, it has only recently been supported by major browsers, offering developers powerful new ways to style based on the presence of child elements.

The `:has()` pseudo-class allows developers to select a parent element if it contains certain child elements. Before `:has()`, CSS was limited in targeting parent elements based on their children, forcing developers to rely on JavaScript for such tasks. This feature fundamentally changes how developers approach CSS, enhancing the expressiveness and control over styling elements within the DOM structure.

For instance, you might want to apply a particular style to a `<div>` only if it contains a specific child element, say an `<img>`. The `:has()` selector makes this possible:

```css
div:has(> img) {
  border: 2px solid green;
}
```

In this example, any `<div>` that directly contains an `<img>` will have a green border applied. This dynamic styling previously required DOM manipulation through JavaScript but can now be efficiently handled with just CSS.

One of the most compelling aspects of the `:has()` pseudo-class is its versatility. Whether you need to manipulate layouts based on content presence or trigger changes for nested interactive elements, `:has()` becomes an invaluable tool. It simplifies otherwise complex CSS logic by consolidating it within stylesheets rather than spreading it between CSS and scripts.

Despite its usefulness, there are caveats. Browser support for `:has()` was limited for some time, but it has improved significantly. As of late 2023, the most recent versions of Chrome, Firefox, Safari, and Edge support the `:has()` pseudo-class. However, developers need to be cautious when using it, ensuring that their target audience has browsers up-to-date enough to support this feature reliably.

In modern web development workflows that prioritize progressive enhancement, `:has()` can be a powerful feature while being guarded with proper fallbacks or feature detection strategies for legacy browsers. Moreover, performance considerations should not be overlooked, as this selector can be costly if applied to a large number of elements or deeply nested structures.

In summary, the introduction of `:has()` opens up new frontiers in CSS, allowing for more semantic and cleaner code by reducing the need for JavaScript for parent-child relationship styling. Its thoughtful use can streamline your CSS, making your stylesheets more efficient and easier to read while aligning with modern web standards.
