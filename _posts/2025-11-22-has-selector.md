---
title: "has() selector"
date: 2025-11-22
categories: ["CSS"]
tags: [has() selector]
layout: single
---

The CSS `has()` selector is a relatively recent addition to the ever-evolving suite of CSS tools, having been introduced in the CSS Selectors Level 4 specification. As of 2023, this feature is becoming more widely supported across modern browsers and offers a powerful new way to select elements based on their descendants.

At its core, the `has()` pseudo-class is used to select an element if it contains a child element that matches a specified selector. This grants developers a parent-selector capability that was previously only accessible through JavaScript or intricate CSS workarounds.

Consider a typical scenario in a web application: a form setup where you wish to highlight parent `<div>` elements that contain a specific invalid input to assist user error resolution. With traditional CSS, there is no direct way to target parents based on the state of a descendant. However, `has()` changes this dynamic.

Here's a simple example:

```html
<form>
  <div class="form-group">
    <input type="text" required>
  </div>
  <div class="form-group">
    <input type="email" required>
  </div>
  <div class="form-group">
    <input type="text" required>
  </div>
</form>
```

To highlight `form-group` divs with empty inputs, one might write:

```css
.form-group:has(input:invalid) {
  border: 1px solid red;
}
```

In this example, the `has()` selector applies a border to any `.form-group` div containing an invalid input, thereby visually indicating an error directly on the ancestor element.

The utility of the `has()` selector today is immense. It reduces reliance on JavaScript for dynamic styling and enhances CSS's declarative nature. This inclusion in your CSS toolkit allows for more semantically meaningful style sheets and can improve performance by reducing DOM manipulation with JavaScript.

However, as with any cutting-edge feature, there's a caveat concerning browser support. The `has()` selector is supported in versions of major browsers like Chrome and Edge starting from 105, Safari from 15.4, and Firefox from 103. However, full cross-browser compatibility is still catching up, notably lagging in some old browser versions. It’s always a good practice to verify current browser support using resources like MDN Web Docs or Can I use before implementing it in production environments.

To employ the `has()` selector safely, consider feature detection and progressive enhancement strategies, ensuring legacy browsers still receive a usable, if not fully-featured, version of your site.

In conclusion, the `has()` selector represents a significant leap forward for CSS, allowing developers to target elements in a way that promotes cleaner and more efficient code. As browser support continues to expand, it's poised to become an essential part of CSS development practices.
