---
title: "paint() function"
date: 2026-05-24
categories: ["CSS"]
tags: [paint() function]
layout: single
---

The CSS `paint()` function, part of the CSS Houdini effort, was introduced to enhance the capability of CSS by allowing developers to define custom painting functions. CSS Houdini is a collection of APIs that give developers deeper control over the CSS rendering process. The `paint()` function is specifically tied to the Paint API, which became more widely available in browsers around the end of the 2010s.

The `paint()` function permits developers to write custom graphics for CSS properties by using a simple JavaScript class. This function empowers web developers to create highly dynamic styles without needing to rely on images or complex workarounds. To utilize this feature, developers write a paint worklet—a JavaScript module that defines the painting logic.

Here's a basic example:

First, you register your paint worklet:

```javascript
if (CSS.paintWorklet) {
  CSS.paintWorklet.addModule('path/to/your-paint-worklet.js');
}
```

Next, you create a `paint-worklet.js` file, which could look something like this:

```javascript
class MyCirclePainter {
  paint(ctx, size, properties) {
    const radius = Math.min(size.width, size.height) / 2;
    ctx.beginPath();
    ctx.arc(size.width / 2, size.height / 2, radius, 0, 2 * Math.PI);
    ctx.fillStyle = 'skyblue';
    ctx.fill();
  }
}

registerPaint('circle', MyCirclePainter);
```

In your CSS, you then apply this custom paint using the `paint()` function:

```css
.circle {
  width: 100px;
  height: 100px;
  background: paint(circle);
}
```

The utility of the `paint()` function today is substantial, as it provides a mechanism for extending CSS with custom drawings while maintaining performance optimizations inherent to the CSS paint pipeline. This is particularly useful for web developers looking to create custom backgrounds, borders, or other stylistic elements that aren't limited by predefined CSS capabilities.

However, the feature does come with caveats, primarily surrounding browser support. As of now, full support is available in Chrome and Edge, while other browsers like Firefox and Safari lag behind, which can limit its application for web projects requiring cross-browser compatibility. Developers need to use feature detection and provide fallbacks for unsupported browsers to ensure a consistent user experience.

Despite these concerns, the `paint()` function is an exciting frontier in CSS, allowing developers to push the boundaries of what can be achieved with web styling, bringing creative and unique visual effects directly into the designer’s toolkit without the overhead of non-performant methods. As browser support continues to expand, so too will the potential for more dynamic and interactive web designs.
