---
title: "has selector"
date: 2026-06-07
categories: ["CSS"]
tags: [has selector]
layout: single
---

The CSS `:has()` pseudo-class selector is an exciting addition to the modern CSS landscape, introduced with the release of CSS Selectors Level 4. Embraced by web developers for its ability to select parents based on their children, this versatile tool offers dynamic styling opportunities and greater control within the DOM structure.

The `:has()` pseudo-class acts as a parent or ancestor selector, allowing elements to be styled conditionally based on the presence of one or more specific child elements. This elevates CSS from merely styling elements based on their inherent properties or direct parents to considering the context of descendant elements. Unlike previous CSS capabilities, the `:has()` selector allows for backwards selection, enabling complex and expressive querying scenarios that were previously accessible only through JavaScript.

Here's a practical example to illustrate its usage:

```css
/* Style a 'parent' div if it contains an 'img' element */
.parent:has(img) {
  border: 2px solid green;
}

/* Target input field labels containing any invalid input */
label:has(input:invalid) {
  color: red;
  font-weight: bold;
}
```

In the examples above, a border is applied to a `div` with the class `parent` if it contains an `img` element as a child, and any `label` containing an `input` that is invalid will be styled with red, bold text. This elevates CSS beyond simple styles, supporting more interactivity without additional markup or relying heavily on JavaScript.

The `:has()` pseudo-class is particularly useful today in scenarios where developers seek to leverage more semantic and accessible designs, especially for designing responsive layouts or enhancing user interfaces dynamically. It refines the styling process by providing a declarative approach to conditionally applied styles and improving the flexibility of CSS applications.

Despite its excitement and potential, the `:has()` selector comes with caveats, particularly in terms of browser support. As of October 2023, major browsers such as Chrome, Edge, and Safari have embraced this feature, but support in Firefox is pending or needs to be enabled via flags. Developers must consider using feature detection or fallbacks to ensure consistent cross-browser performance.

In conclusion, the CSS `:has()` selector is a powerful addition to the toolkit of modern web developers, offering a deeper level of control over how document structures are styled dynamically. It exemplifies the ongoing evolution of CSS towards more responsive and interactive web design, although attention to browser compatibility remains paramount to leveraging its full potential in production environments.
