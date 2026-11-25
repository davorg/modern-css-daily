---
title: "text-decoration-inset"
date: 2026-11-25
categories: ["CSS"]
tags: ["text-decoration-inset"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-decoration-inset-property"
---

`text-decoration-inset` controls how far a text decoration—such as an underline, overline, or line-through—is inset from the start and end of the decorated text. It lets you shorten the decoration without changing the text’s layout or replacing the line with a border or pseudo-element.

The property is defined in CSS Text Decoration Module Level 4. That specification is still a draft, so details may change as the standard develops.

A single length applies the same inset at both ends:

```css
a {
  text-decoration-line: underline;
  text-decoration-inset: 0.2em;
}
```

Two values set the start and end insets respectively:

```css
a {
  text-decoration-line: underline;
  text-decoration-inset: 0.2em 0.4em;
}
```

This is useful when a full-width decoration feels visually heavy. For example, underlines in navigation links, tabs, headings, or compact interface controls can look more intentional when they stop slightly inside the text’s edges. Using `em` units also allows the inset to scale with the element’s font size.

The property complements existing decoration controls rather than replacing them. `text-underline-offset` changes an underline’s vertical position, while `text-decoration-thickness` changes its thickness. By contrast, `text-decoration-inset` changes the line’s extent along the text.

It can be useful today as a progressive enhancement. If a browser does not recognize the property, it ignores the declaration and keeps the ordinary full-length decoration. That makes a standard underline a straightforward fallback:

```css
.nav-link {
  text-decoration: underline;
  text-decoration-inset: 0.15em;
}
```

The main caveat is browser interoperability. Because this is a draft Level 4 feature, do not assume that every browser used by your audience supports it consistently. Check current compatibility information and test the browsers relevant to your project. Avoid making the inset essential to readability, interaction, or state indication; the undecorated inset should be a visual refinement, not the only way users can identify a link or selected item.

Further reading: [CSS Text Decoration Module Level 4 — `text-decoration-inset`](https://drafts.csswg.org/css-text-decor-4/#text-decoration-inset-property)
