---
title: "has() pseudo-class with container queries"
date: 2026-06-11
categories: ["CSS"]
tags: [has() pseudo-class with container queries]
layout: single
---

In the ever-evolving landscape of CSS, the introduction of the `has()` pseudo-class combined with container queries represents a significant advancement for web developers, enhancing the flexibility and responsiveness of modern web design. Introduced in 2023 as part of the latest updates to the CSS specification, the `has()` pseudo-class brings a level of interactivity and context-based styling that was difficult to achieve with CSS alone.

The power of the `has()` pseudo-class lies in its ability to apply styles based on the presence of a condition—in this case, the existence of specific elements within a container. When used with container queries, `has()` allows developers to query and conditionally style an element based on its descendants.

Consider the following example, where traditional styling techniques fall short. Suppose you have a card component that should only display a border if it contains an image. Utilizing the `has()` pseudo-class, this requirement is easily met:

```css
.card:has(img) {
  border: 2px solid #000;
}
```

In this scenario, the `.card` element will acquire a border only if it contains an `<img>` tag. This can be particularly useful for content-heavy sites where components dynamically change based on user input or data conditions.

Now, imagine integrating this with container queries to adjust styles based on element size, making your design responsive not just to screen size but to the element's context:

```css
@container (min-width: 300px) {
  .card:has(img) {
    display: flex;
    padding: 16px;
  }
}
```

In this example, when the container where `.card` resides has a minimum width of 300px and contains an image, it applies flexbox layout and padding, ensuring optimal design without JavaScript or complicated CSS structures.

The utility of the `has()` pseudo-class with container queries is evident in how it simplifies conditional styling, significantly reducing the need for JavaScript in managing component state. It delivers a declarative way to achieve dynamic styles, enhancing maintainability and readability.

However, as with any new development in web technologies, there are caveats. As of now, browser support is varied. While the latest versions of Chrome, Edge, and Firefox are rolling out support, Safari and some older browsers may lag. Therefore, it's essential to incorporate feature detection or progressive enhancement strategies to ensure a graceful degradation of functionality.

The integration of the `has()` pseudo-class within container queries marks a step forward in CSS capabilities, allowing web developers to create responsive, intuitive designs without the overhead of additional JavaScript, aligning with modern-day demands for performance and efficiency in web development.
