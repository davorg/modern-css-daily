---
title: "text-decoration-line"
date: 2026-10-04
categories: ["CSS"]
tags: ["text-decoration-line"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-3/#text-decoration-line-property"
---

`text-decoration-line` controls which decorative lines are drawn on an element’s text. It is the longhand behind part of the `text-decoration` shorthand and supports `none`, `underline`, `overline`, `line-through`, and `blink`. The line keywords can be combined when more than one decoration is needed.

The property is defined in CSS Text Decoration Module Level 3. The linked specification is the CSS Working Group’s current Editor’s Draft rather than a final W3C Recommendation; no precise introduction date should be inferred from that status.

A minimal example looks like this:

```css
a {
  text-decoration-line: underline;
}

.edited {
  text-decoration-line: underline line-through;
}
```

Using the longhand is helpful when you want to change the type of decoration without resetting other decoration properties. For example, an element might already have a `text-decoration-color` or `text-decoration-style`; changing only `text-decoration-line` leaves those declarations intact. By contrast, setting the `text-decoration` shorthand can reset omitted components to their initial values.

The property is useful for familiar interface conventions such as underlining links, striking out unavailable items, or combining an underline and overline for specialized typography. It also makes component styles easier to maintain because the presence of a line can be controlled separately from its appearance.

There are several caveats. Although `text-decoration-line` is not inherited, decorations can propagate from an ancestor across descendant text. Consequently, applying `text-decoration-line: none` to a child does not necessarily remove a line established by its ancestor. If a decoration must stop at a particular boundary, structure and layout may need to be adjusted rather than relying on `none`.

The `blink` keyword is part of the specified syntax, but the specification allows user agents not to render blinking text. It should not be used for essential feedback, and blinking content can also create accessibility problems.

Decorations are presentational rather than semantic. For example, use appropriate HTML such as `<del>` when text represents a deletion, rather than relying on `line-through` alone. Likewise, do not communicate state solely through an underline or strike-through. Test the values and combinations you use in the browsers required by your project instead of assuming identical rendering.

Further reading: [CSS Text Decoration Module Level 3 — `text-decoration-line`](https://drafts.csswg.org/css-text-decor-3/#text-decoration-line-property)
