---
title: "has() pseudo-class"
date: 2025-09-20
categories: ["CSS"]
tags: [has() pseudo-class]
layout: single
---

As web developers continually seek ways to enhance user interfaces and boost the user experience, CSS has evolved, offering more sophisticated and dynamic styles. Among the newer additions to CSS selectors is the `has()` pseudo-class, a powerful feature that provides developers with unprecedented ways to craft complex, context-sensitive styles. This pseudo-class was introduced with the Selectors Level 4 specification and is now seeing adoption in modern web projects as browser support expands.

The `has()` pseudo-class is somewhat akin to a "parent selector." It allows you to apply styles to elements based on whether they possess a specified child element or not. In essence, it lets you style an element if it "has" certain elements within it.

For example, consider a scenario where you have a list of items, and you want to style list items that contain a nested `span`. With `has()`, this is straightforward:

```css
ul li:has(span) {
  color: red;
}
```

In this snippet, any `li` that contains a `span` element will be styled with a red text color. The `has()` pseudo-class acts as a parent selector by inspecting its descendants, something previously challenging to achieve solely with CSS.

The utility of the `has()` pseudo-class lies in its ability to eliminate the need for additional JavaScript or class manipulation to achieve certain style changes, thereby streamlining the styling process and reducing code complexity. This can be particularly useful in form styling, UI components that rely on state changes, and interactive visual effects.

For instance, you might use `has()` to alter the appearance of a button or input field that contains specific user input:

```css
input:has([value]) {
  border-color: green;
}
```

This rule would style any input field with a value with a green border, providing immediate visual feedback.

However, the `has()` pseudo-class is not without its caveats. Its browser support, while improving, is not yet universal. As of now, it is fully supported in modern versions of Chrome and other Chromium-based browsers, as well as more recent versions of Firefox and Safari. Always check the current compatibility tables, as the landscape of web development evolves rapidly.

Additionally, complex queries written with `has()` could potentially lead to performance issues, especially on pages with a significant number of elements or deep nesting. Developers should use it judiciously and test its impact on their specific web applications.

In conclusion, the `has()` pseudo-class introduces a new dimension to CSS, empowering developers to define styles based on structural relationships, simplifying codebases, and enhancing the interactive capabilities of web pages. As compatibility improves, it promises to become an indispensable tool in modern web design.
