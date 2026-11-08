---
title: "text-decoration-skip-self"
date: 2026-11-08
categories: ["CSS"]
tags: ["text-decoration-skip-self"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-decoration-skip-self-property"
---

CSS text decorations have an important quirk: they are propagated through an element’s inline descendants rather than inherited like ordinary properties. Consequently, applying `text-decoration: none` to a child does not remove an underline established by its ancestor.

`text-decoration-skip-self` provides a direct way for an element to opt out of those decorations. Its current syntax accepts two values:

- `auto`, the initial value, applies decorations normally.
- `skip-all` skips any text decorations that would affect the element.

A common use case is excluding a badge, label, or other nested content from a link’s underline:

```html
<a class="article-link" href="/article">
  Read the article
  <span class="badge">New</span>
</a>
```

```css
.article-link {
  text-decoration: underline;
}

.badge {
  text-decoration-skip-self: skip-all;
}
```

Here, the link remains underlined while the badge is excluded from the decoration. In browsers that do not implement the property, the declaration is ignored and the badge remains underlined—a generally usable fallback.

This capability is useful because existing workarounds often require changing markup or replacing native text decoration with a visual approximation such as a background gradient or border. Those alternatives can become fragile when text wraps, font metrics change, or decorations need to follow writing modes and text layout. `text-decoration-skip-self` preserves the browser’s normal decoration behavior while allowing a specific element to opt out.

The feature is defined in the CSS Text Decoration Module Level 4 draft. It should therefore be treated as an evolving standards feature rather than a universally available baseline. Implementation may vary across browsers, and the draft itself can still change. Check compatibility for the browsers your project supports, retain a reasonable fallback, and test combinations involving nested decorations and inline layout.

It is also important not to confuse this property with `text-decoration-skip-ink`, which controls whether an underline avoids glyph shapes. `text-decoration-skip-self` instead controls whether a particular element participates in the decoration at all.

Further reading: [CSS Text Decoration Module Level 4 — `text-decoration-skip-self`](https://drafts.csswg.org/css-text-decor-4/#text-decoration-skip-self-property)
