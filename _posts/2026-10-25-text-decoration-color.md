---
title: "text-decoration-color"
date: 2026-10-25
categories: ["CSS"]
tags: ["text-decoration-color"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-3/#text-decoration-color-property"
---

`text-decoration-color` controls the color of text decoration lines, such as underlines, overlines, and line-throughs. It lets the decoration use a different color from the text itself.

The property is defined in the CSS Text Decoration Module Level 3, a standards-track draft from the CSS Working Group. The draft remains subject to the standards process, but the property uses established CSS syntax and can be adopted as a progressive enhancement without relying on a particular introduction date.

A minimal example looks like this:

```css
a {
  color: #0645ad;
  text-decoration-line: underline;
  text-decoration-color: #e63946;
}
```

Here, the link text is blue while its underline is red. `text-decoration-color` accepts a CSS `<color>` value. Its initial value is `currentcolor`, so without an explicit declaration, the decoration uses the element’s current text color.

Separating these colors can improve visual hierarchy. For example, links can retain a readable text color while using a brand or accent color for their underlines. The property is also useful for indicating states such as hover, focus, validation, or editorial annotations without changing the text itself.

```css
a:hover,
a:focus-visible {
  text-decoration-color: orange;
}
```

There are a few important caveats. First, this property only changes color: it does not create a decoration. Use `text-decoration-line` or another declaration that establishes an underline, overline, or line-through. Other aspects, such as line style and thickness, are controlled by separate text-decoration properties.

Second, `text-decoration-color` is not inherited. Text decorations also have propagation rules of their own: a decoration established by an ancestor may continue across descendant text, and changing the property on a descendant does not generally recolor the ancestor’s decoration.

As with any visual styling, do not rely on decoration color alone to communicate essential information. Ensure sufficient contrast and preserve other cues—such as the underline itself, text, or icons—for users who cannot distinguish particular colors.

If compatibility with older or specialized user agents matters, test against your project’s actual browser requirements. When the declaration is not applied, the decoration can still use its ordinary color, making this feature suitable for graceful enhancement.

**Further reading:** [CSS Text Decoration Module Level 3: `text-decoration-color`](https://drafts.csswg.org/css-text-decor-3/#text-decoration-color-property)
