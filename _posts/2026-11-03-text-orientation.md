---
title: "text-orientation"
date: 2026-11-03
categories: ["CSS"]
tags: ["text-orientation"]
layout: single
source: "https://drafts.csswg.org/css-writing-modes-4/#text-orientation"
---

`text-orientation` controls how characters are displayed within vertical lines of text. It is useful when `writing-mode` is set to a vertical mode such as `vertical-rl` or `vertical-lr`; it has no effect in horizontal writing modes.

The property is defined in CSS Writing Modes Level 4, currently published as an Editor’s Draft. That means it is part of ongoing standards work and may still be refined.

Its current syntax provides three values:

- `mixed` — the initial value. Characters intended for vertical typesetting remain upright, while characters normally used horizontally, such as many Latin letters, are displayed sideways.
- `upright` — displays all characters upright. For example, the letters in an English acronym appear individually upright rather than as a rotated horizontal word.
- `sideways` — displays all text sideways, as though it had first been laid out horizontally and then rotated according to the vertical writing mode.

A minimal example:

```html
<p class="vertical-label">CSS 仕様</p>
```

```css
.vertical-label {
  writing-mode: vertical-rl;
  text-orientation: upright;
}
```

Here, the paragraph flows vertically from right to left, and every character remains upright.

The feature is especially valuable for vertical Japanese and other East Asian typography, where different scripts can require different orientations in the same line. It can also help with compact interface labels, diagrams, book-like layouts, and decorative headings. Unlike applying `transform: rotate(...)`, `text-orientation` participates in vertical text layout: line flow, character placement, and inline progression continue to follow the selected writing mode.

There are several caveats. First, `text-orientation` does not make text vertical by itself; you must also choose an appropriate `writing-mode`. Second, `upright` treats characters individually, so it is not equivalent to rotating an entire word or phrase. The actual glyphs and positioning can also depend on the font and on Unicode character-orientation data.

Finally, browser behavior should be tested for the specific scripts, fonts, and layout combinations your project uses. A readable fallback is generally straightforward because unsupported declarations are ignored, but a design that depends on vertical dimensions may still need alternative spacing or sizing.

Further reading: [CSS Writing Modes Level 4 — Text Orientation](https://drafts.csswg.org/css-writing-modes-4/#text-orientation)
