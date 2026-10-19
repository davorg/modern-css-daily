---
title: "text-decoration-skip-box"
date: 2026-10-19
categories: ["CSS"]
tags: ["text-decoration-skip-box"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-decoration-skip-box-property"
---

`text-decoration-skip-box` controls whether a text decoration drawn by an ancestor continues through an element’s box. It is useful when an underline, overline, or line-through should flow across ordinary text but leave a gap around an embedded element such as an icon, badge, or inline control.

The property accepts two values:

- `none`, the initial value, does not skip the box.
- `all` skips the element’s entire margin box when painting decorations that originate from an ancestor.

A minimal example:

```html
<p class="notice">
  Read the documentation
  <span class="badge">New</span>
  before upgrading.
</p>
```

```css
.notice {
  text-decoration: underline;
}

.badge {
  text-decoration-skip-box: all;
}
```

Here, the paragraph supplies the underline. Setting `text-decoration-skip-box: all` on the badge asks the browser to interrupt that ancestor decoration around the badge’s margin box. Decorations originating on the badge itself are not skipped.

This solves a different problem from `text-decoration-skip-ink`. Ink skipping avoids drawing a decoration through parts of glyphs, such as letter descenders. Box skipping creates a break around an entire element, including non-text content. That makes it useful for mixed inline layouts containing icons, labels, annotations, or replaced elements where a continuous line would look cluttered or imply that the embedded item is part of the decorated text.

`text-decoration-skip-box` is defined in the Editor’s Draft of CSS Text Decoration Module Level 4. It remains a draft feature rather than a fully settled, universally implemented part of the platform. Its syntax or behavior could still change as the specification develops.

Browser support should therefore be treated as a progressive enhancement. Check current compatibility data and test in the browsers relevant to your project. Browsers that do not recognize the property will ignore the declaration, leaving the ancestor’s decoration uninterrupted. Design that fallback deliberately, and avoid relying on box skipping to communicate essential state or meaning.

The feature is useful today when supported because it provides a direct, declarative alternative to masking decorations, adding background-colored patches, or splitting linked text into multiple decorated fragments.

Further reading: [CSS Text Decoration Module Level 4 — `text-decoration-skip-box`](https://drafts.csswg.org/css-text-decor-4/#text-decoration-skip-box-property)
