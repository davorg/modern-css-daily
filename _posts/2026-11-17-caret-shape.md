---
title: "caret-shape"
date: 2026-11-17
categories: ["CSS"]
tags: ["caret-shape"]
layout: single
source: "https://drafts.csswg.org/css-ui-4/#caret-shape"
---

`caret-shape` controls the visual form of the text insertion caret—the marker showing where typed text will appear in an editable element. It does not affect the mouse pointer or the appearance of selected text.

The property is defined in the CSS Basic User Interface Module Level 4 specification. That specification is still a draft, so `caret-shape` should be treated as an emerging feature rather than a universally available part of the web platform.

The specified values are:

- `auto`: lets the user agent choose the caret shape.
- `bar`: displays a thin line perpendicular to the text’s inline axis.
- `block`: displays a block-shaped caret.
- `underscore`: displays a thin line parallel to the inline axis.

Because the definitions use the inline axis, they also make sense in writing modes where text does not run horizontally.

A minimal example applies a block caret to an editable region:

```html
<div class="editor" contenteditable="true">
  Edit this text
</div>
```

```css
.editor {
  caret-shape: block;
}
```

This can be useful for interfaces that imitate terminals, command palettes, code editors, or modal editing environments. A block caret can make an editing mode feel distinct, while an underscore caret may better match a particular application style. The property provides a declarative alternative to building and positioning a simulated caret with JavaScript and extra markup.

`caret-shape` can also be used alongside `caret-color`, which controls the caret’s color:

```css
.editor {
  caret-shape: block;
  caret-color: lime;
}
```

The main caveat is browser support. Implementations may be limited or inconsistent, and support should not be assumed without testing in the browsers relevant to your project. Avoid making the caret shape the only indication of application state or editing mode. If a browser does not recognize the declaration, it will continue using its normal caret behavior.

For progressive enhancement, feature queries can isolate related styling:

```css
@supports (caret-shape: block) {
  .editor {
    caret-shape: block;
  }
}
```

Even where supported, the exact rendering remains under the browser’s control and may reflect platform conventions. Test with different writing modes, zoom levels, and editable controls, and ensure that the default caret remains usable when the property is unavailable.

Further reading: [CSS Basic User Interface Module Level 4 — `caret-shape`](https://drafts.csswg.org/css-ui-4/#caret-shape)
