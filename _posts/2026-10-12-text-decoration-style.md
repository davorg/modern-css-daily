---
title: "text-decoration-style"
date: 2026-10-12
categories: ["CSS"]
tags: ["text-decoration-style"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-decoration-style-property"
---

`text-decoration-style` controls the visual style of text-decoration lines, such as underlines, overlines, and line-throughs. It does not create a decoration by itself; that is the job of `text-decoration-line` or the `text-decoration` shorthand.

The property accepts five keyword values:

- `solid`
- `double`
- `dotted`
- `dashed`
- `wavy`

Its initial value is `solid`. A minimal example is:

```css
a {
  text-decoration-line: underline;
  text-decoration-style: wavy;
}
```

The same result can be expressed with the shorthand:

```css
a {
  text-decoration: underline wavy;
}
```

The property is defined in CSS Text Decoration Module Level 4. The cited specification is an Editor’s Draft, meaning it is active CSS Working Group work rather than a finalized Recommendation. Avoid attaching a precise “introduced in” date to the feature; CSS modules and browser implementations evolve independently.

`text-decoration-style` is useful because it provides a native way to distinguish different kinds of decorated text. A solid underline might indicate an ordinary link, while a wavy underline could mark an issue or annotation. Dotted, dashed, and double lines can also add visual hierarchy without using extra elements, background images, or border-based approximations.

Native text decorations generally behave better than `border-bottom` for inline text. They follow text across line breaks and participate in the rest of the CSS text-decoration model, including decoration color and thickness.

There are several caveats. First, line style alone should not carry essential meaning: users may not notice the difference, and visual rendering can vary. Pair stylistic distinctions with text, icons, semantics, or other accessible cues where necessary.

Second, text-decoration properties are not inherited in the usual CSS sense, but decorations can propagate through descendant inline content. If an ancestor establishes an underline, changing `text-decoration-style` on a descendant does not necessarily restyle that ancestor’s decoration. Apply the style on the element that establishes the decoration.

Finally, test the values you intend to use in your supported browsers and rendering environments. Exact appearance can differ with typography, decoration thickness, zoom, and the browser’s renderer. Wavy or dotted lines should therefore be treated as presentational choices, not pixel-identical graphics.

Further reading: [CSS Text Decoration Module Level 4 — `text-decoration-style`](https://drafts.csswg.org/css-text-decor-4/#text-decoration-style-property)
