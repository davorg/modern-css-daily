---
title: "display: contents"
date: 2026-03-07
categories: ["CSS"]
tags: [display: contents]
layout: single
---

The CSS property `display: contents` was introduced in the CSS Display Module Level 3, with initial drafts surfacing around 2017. Designed to offer a new layer of flexibility for web developers, it represents a notable shift in how elements can be manipulated within the document's flow.

Essentially, `display: contents` applies to an element making it disappear from the DOM tree's layout tree. It allows its child elements to seamlessly replace it, stepping up to the place of their parent without discontinuing the document flow. The parent element's box is flattened, meaning it's removed from the layout, and only its children are considered for rendering, inheriting styles as they would if their parent was displayed normally.

Here's a simple example to illustrate its use:

```html
<style>
  .parent {
    display: contents;
  }

  .child {
    padding: 10px;
    background-color: lightblue;
    border: 1px solid navy;
  }
</style>

<div class="parent">
  <div class="child">Child 1</div>
  <div class="child">Child 2</div>
</div>
```

In the above example, the `.parent` element has a `display` value of `contents`, which means it won’t have borders, padding, or margins affecting the layout. The children, `.child`, take on their display properties directly in the HTML structure as if they were not nested inside a parent division.

The utility of `display: contents` becomes evident particularly when dealing with CSS Grid or Flexbox layouts. When you want to style individual items as part of these robust layout systems without an intermediate container influencing the visual architecture, `display: contents` can ensure an optional cleanup of layout without disturbing the semantic HTML structure.

However, it's important to recognize the limitations and quirks of using `display: contents`. One of the primary caveats is its limited browser support. Although most modern browsers like Chrome, Firefox, and Safari have adopted the feature, as of late 2023, Internet Explorer and some older versions of Edge do not support it fully. Additionally, `display: contents` can update the document structure in ways that affect accessibility technologies. The visual disappearance of a parent can sometimes remove semantic meaning or structure that screen readers rely on, making accessibility considerations crucial when employing this feature.

Despite these potential hurdles, `display: contents` remains a powerful tool in the modern web developer's CSS toolkit, offering newfound flexibility and streamlined control over complex layouts. With a keen eye on semantics and browser capability checks, it provides a sophisticated solution for clean, effective design.
