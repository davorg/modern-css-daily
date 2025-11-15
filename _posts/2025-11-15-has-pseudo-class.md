---
title: "has pseudo-class"
date: 2025-11-15
categories: ["CSS"]
tags: [has pseudo-class]
layout: single
---

The CSS `:has()` pseudo-class, introduced in the CSS Selectors Level 4 specification, is a powerful new tool for web developers. It's akin to a parent selector, allowing you to apply styles based not just on an element’s own properties but on whether it contains or is followed by child elements of a certain structure or type. This ability to influence styling based on child elements fundamentally transforms how developers can approach CSS, enabling more dynamic design patterns.

The primary feature of the `:has()` pseudo-class is its capability to select an element if at least one of the selectors passed as an argument matches any of its descendants. This opens up a wide range of possibilities for styling elements conditionally. Unlike most CSS selectors that operate from top-down, `:has()` gives CSS a bidirectional design capability, which can reduce reliance on scripting for effects like toggling styles, complex tree structures, and more.

Here’s a basic example of how `:has()` can be used:

```css
/* Select any `.card` that contains an image and apply a border */
.card:has(img) {
   border: 2px solid green;
}
```

In this scenario, any `.card` element that contains an `<img>` element will have a green border applied. This style can dynamically change as HTML content is modified, which is particularly useful for templates and themes where content structure can change but styles need to remain consistent.

Why is `:has()` useful today? It empowers developers to create cleaner, more maintainable CSS. Before this, applying certain styles conditionally based on a parent-child relationship required JavaScript interventions or non-semantic CSS hacks that cluttered the codebase. With `:has()`, CSS can handle specific conditions that previously necessitated more complex JavaScript logic, such as determining if a dropdown should display a certain style based on whether it contains any items.

However, while this feature is a game-changer, developers should be mindful of its current browser support. As of now, `:has()` is widely supported in major browsers like Chrome, Edge, and Safari, but its support in Firefox is still developing. This discrepancy reinforces the importance of feature detection and progressive enhancement strategies to ensure your web application functions correctly across all user environments.

In summary, the introduction of the `:has()` pseudo-class in CSS enhances the language's capacity to handle complex styling scenarios with succinct, readable, and efficient code, marking a significant step forward in web design capabilities. However, developers should remain cautious and verify browser support to maximize compatibility and user experience.
