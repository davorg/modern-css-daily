---
title: "scroll-timeline-axis"
date: 2026-01-06
categories: ["CSS"]
tags: [scroll-timeline-axis]
layout: single
---

In the ever-evolving world of CSS, new features continually emerge to provide developers with tools to create more interactive and visually appealing web experiences. One such innovative feature is the `scroll-timeline-axis`, a part of the CSS Scroll-Linked Animations module introduced in 2023. This feature allows developers to control animations based on the scroll position of a webpage or an element, offering a new dimension of interactivity and engagement.

The `scroll-timeline-axis` property is used to define the direction of scrolling that will influence the linked animations. It can be set to either the `block` or `inline` value, indicating whether the scroll direction is vertical or horizontal, respectively. This is particularly useful for scenarios where you want animations to be triggered as users navigate through content, either by scrolling up and down (block) or left to right (inline).

Here's an example of how to use `scroll-timeline-axis` in a practical way:

```css
@scroll-timeline myScrollTimeline {
  source: auto;
  axis: block;
}

.box {
  animation: slideIn 1s both;
  animation-timeline: myScrollTimeline;
}

@keyframes slideIn {
  0% {
    transform: translateX(-50%);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}
```

In this example, a scroll timeline named `myScrollTimeline` dictates the animation of a `.box` element. The `axis: block;` line specifies that the animation should respond to vertical scrolling. As users scroll down the page, the `slideIn` animation plays, bringing the `.box` element into view.

The introduction of `scroll-timeline-axis` comes in response to the growing demand for responsive and dynamic content presentation on the web. This feature enables developers to craft experiences that are not only reactive but also engaging, making browsing more intuitive and visually appealing.

Despite its potential, there are caveats, primarily revolving around browser support. As of its introduction, `scroll-timeline-axis` is supported in the latest versions of major browsers like Chrome and Edge, but support in Firefox and Safari is either limited or planned for future releases. This disparity necessitates that developers check the current support landscape and consider fallbacks or progressive enhancement to maintain cross-browser compatibility.

The `scroll-timeline-axis` is a powerful addition to the CSS toolbox, offering new possibilities for scroll-linked animations and user interaction. While still emerging and subject to browser support limitations, it stands as a clear indicator of the exciting future for CSS and web development.
