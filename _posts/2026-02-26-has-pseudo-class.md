---
title: "has pseudo-class"
date: 2026-02-26
categories: ["CSS"]
tags: [has pseudo-class]
layout: single
---

The `:has()` pseudo-class is a powerful addition to the CSS toolbox, ushered in with the release of CSS Selectors Level 4. This feature was first consistently supported by major browsers starting around 2022, marking a significant shift in how developers can leverage styles based on the presence of child elements.

Traditionally, CSS operates in a hierarchal manner, affecting child elements of a parent selector. The `:has()` pseudo-class allows CSS to break free from this one-directional relationship by providing the ability to select elements based on their children or subsequent elements. In essence, it can be considered as a parent selector in CSS.

Consider a scenario where you want to style a list item containing a specific child element, like an image. The `:has()` pseudo-class enables this with ease:

```css
li:has(img) {
  font-weight: bold;
  background-color: #f0f0f0;
}
```

In this example, any `<li>` element containing an `<img>` child will receive the specified styling, making the list item bold with a light gray background. Prior to the introduction of `:has()`, achieving this effect would have required JavaScript intervention.

The utility of `:has()` is particularly pronounced today, as web applications grow increasingly dynamic and interactive. Whether it's for designing responsive layouts or interactive UIs, being able to apply styles based on sibling or child content without additional scripting is invaluable. It improves style encapsulation and reduces dependency on JavaScript for these specific tasks, contributing to cleaner and more maintainable codebases.

Despite its usefulness, developers should be cautious of certain caveats, particularly regarding browser support. As of late 2023, `:has()` enjoys widespread support in modern browsers, including the latest versions of Chrome, Firefox, Safari, and Edge. However, developers working on projects that require compatibility with older browsers, like Internet Explorer, must account for the absence of support for `:has()`. In such cases, it's advisable to implement fallback styles or consider progressive enhancement strategies.

Overall, the `:has()` pseudo-class marks a significant enhancement for CSS, empowering developers to create more intuitive and flexible styles with less effort. By circumventing the limitations of previous CSS versions, it fosters innovative design patterns that can adapt to varying content structures seamlessly. As browser support continues to solidify, `:has()` is set to become a staple in the modern developer's toolkit, driving a new wave of functionality in web design.
