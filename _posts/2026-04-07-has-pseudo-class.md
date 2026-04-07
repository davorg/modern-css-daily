---
title: "has() pseudo-class"
date: 2026-04-07
categories: ["CSS"]
tags: [has() pseudo-class]
layout: single
---

In the ever-evolving world of CSS, the `:has()` pseudo-class is a fairly recent addition that opens a world of possibilities for designing interactive, responsive layouts. Officially introduced in the CSS Selectors Level 4 specification, this powerful feature represents a significant leap forward in styling capabilities, allowing styles to be applied based on the presence of certain children or descendants within an element.

The `:has()` pseudo-class functions as a parent selector, meaning it can target an element if it contains a specific descendant. This conceptually brings logical capabilities to CSS, allowing developers to design more complex and responsive layouts without resorting to JavaScript.

An instance of `:has()` in action could look like this:

```css
/* Highlight a section only if it contains an error message */
section:has(.error-message) {
  border: 2px solid red;
}

/* Apply styles to a container if it includes at least one checked checkbox*/
.container:has(input[type="checkbox"]:checked) {
  background-color: #f0f0f0;
}
```

In the first example, sections containing elements with the class `.error-message` will feature a red border, enabling a direct CSS solution for error styling. The second snippet demonstrates a style change in the container based on the presence of a checked checkbox, which is traditionally more cumbersome to achieve without JavaScript.

The `:has()` pseudo-class is a game-changer for several reasons. It reduces the dependency on JavaScript for DOM manipulations, leading to faster performance and simpler maintenance. It enhances how CSS can respond to dynamic content, making it easier to create interactive interfaces with less code.

However, like any new tool in the web development toolkit, `:has()` comes with its caveats. One of the significant considerations is browser support. As of late 2023, while most modern browsers, including the latest versions of Chrome, Edge, and Firefox, support `:has()`, compatibility should be checked for specific cases, especially on older or niche browsers. Internet Explorer and some early versions of Safari have limited or no support, necessitating alternative solutions for comprehensive cross-browser compatibility.

Developers should be mindful that relying heavily on `:has()` during the design phase requires validation of its presence and support in the target browsers. Nonetheless, the potential of this pseudo-class in crafting dynamic styles without JavaScript cannot be overstated, making it a valuable asset for modern web development. As browser support continues to expand, the `:has()` pseudo-class is expected to become an even more pivotal feature in the CSS arsenal.
