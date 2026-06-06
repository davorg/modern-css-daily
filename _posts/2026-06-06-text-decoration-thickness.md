---
title: "text-decoration-thickness"
date: 2026-06-06
categories: ["CSS"]
tags: [text-decoration-thickness]
layout: single
---

As web design continues to evolve, the latest CSS features offer unprecedented control over the aesthetic and functional elements of text styling. One of the more nuanced yet valuable additions to this toolbox is the `text-decoration-thickness` property. This feature, introduced as part of the CSS Text Decoration Module Level 3, allows developers to specify the thickness of text decorations like underlines, offering finer control over text aesthetics.

The `text-decoration-thickness` property enables you to define how thick or thin you want the text decoration to appear. Previously, styling text decorations was fairly limited to basic underlines with preset thicknesses that often didn't align with the creative vision for the text. With this property, designers can now ensure underlines and other decorations match the overall design language of their project by adjusting their thickness to better fit various font sizes and styles.

Here's a quick example to illustrate its usage:

```css
p {
  text-decoration: underline;
  text-decoration-thickness: 3px;
}
```

In this example, any paragraph element with an underline will have a decoration that is 3 pixels thick, providing a bold and clearly visible underline. This is particularly useful for ensuring consistency in designs that use custom typography or where varied header sizes are employed.

One reason why `text-decoration-thickness` is so significant today is because it supports better customization for accessibility-focused design. Designers can create more legible text for users with visual impairments by adjusting underline thicknesses to enhance readability. Additionally, this customization can contribute to creating a more cohesive and visually appealing design.

As with many newer CSS properties, it's important to consider browser support. As of October 2023, `text-decoration-thickness` enjoys widespread support across modern browsers, including the latest versions of Chrome, Firefox, Edge, and Safari. This means that you can confidently use this feature for most web projects without significant fallback considerations.

However, like any other evolving web technology, be mindful of older platforms and devices that might still lack support for this property. Developers can use progressive enhancement techniques to ensure a graceful fallback for those rare instances where the property isn't supported, typically by allowing the default underlining to persist.

In conclusion, `text-decoration-thickness` is a boon for web developers, offering them improved control over text decoration aesthetics. Its introduction has marked a step towards more adaptable and visually appealing text rendering on the web, enhancing both the usability and the beauty of digital interfaces. With solid browser support, this CSS feature is indeed a worthy addition to any modern developer's toolkit.
