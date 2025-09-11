---
title: "has() pseudo-class"
date: 2025-09-11
categories: ["CSS"]
tags: [has() pseudo-class]
layout: single
---

The `has()` pseudo-class is a noteworthy enhancement to modern CSS, introduced as part of the CSS4 Selectors specification. It offers a powerful way to style elements based on their descendants or, more broadly, their children. Initially inspired by some functionalities of JavaScript, `has()` enables developers to apply styles dynamically without needing JavaScript, which can simplify codebases and enhance performance.

Essentially, the `has()` pseudo-class allows you to select an element only if it contains certain other elements within it. This can be especially useful for targeting parent elements based on the state or characteristics of their children. Before its implementation, achieving similar functionality would often require scripting with JavaScript or complex selector workarounds.

### How `has()` Works

The basic syntax for `has()` is simple: `:has(selector)`. This selector targets an element that contains a specific selector inside it. The full supportive power can be realized by combining `has()` with other CSS selectors, enabling complex and responsive design patterns.

### Example Usage

Consider the following HTML snippet:

```html
<div class="card">
    <h2>Title</h2>
    <p>Some description text.</p>
    <button class="cta">Call to Action</button>
</div>

<div class="card">
    <h2>Title</h2>
    <p>Some description text.</p>
</div>
```

Using `has()`, you can style the `.card` element only if it contains a `<button>`:

```css
.card:has(.cta) {
    border: 2px solid #3498db;
    background-color: #eaf4fc;
}
```

In this example, only the first `.card` will have the specified styles because it includes a `.cta` button.

### Why It’s Useful

The `has()` pseudo-class significantly enhances the capabilities of CSS in modern web development by reducing the need for JavaScript for simple interactions. This can lead to cleaner code and improved page load times, as CSS is often faster to execute and more straightforward to maintain than JavaScript for styling purposes.

### Caveats and Browser Support

While `has()` provides a powerful tool for developers, it's essential to be cautious about browser support. As of late 2023, `has()` is well-supported in modern browsers like Chrome, Edge, and Safari. However, its support in Firefox is still under development, and thus, developers should ensure fallback solutions for non-supporting browsers. Utilizing feature queries (`@supports`) can help maintain compatibility and ensure a smooth user experience across different platforms.

In conclusion, the `has()` pseudo-class represents a significant step forward in CSS’s ability to create dynamic and interactive elements. By intelligently embracing its capabilities alongside thoughtful consideration for browser support, developers can harness its power to build more elegant and performant web applications.
