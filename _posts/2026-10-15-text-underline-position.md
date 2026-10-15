---
title: "text-underline-position"
date: 2026-10-15
categories: ["CSS"]
tags: ["text-underline-position"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-underline-position-property"
---

`text-underline-position` controls where CSS places an underline relative to the text it decorates. It does not create an underline by itself; use `text-decoration-line` or the `text-decoration` shorthand for that.

The property is defined in the CSS Text Decoration Module Level 4 Editor’s Draft. As an Editor’s Draft, the specification is still evolving rather than being a finished W3C Recommendation, although the feature is already useful in browsers today.

A minimal example is:

```css
a {
  text-decoration-line: underline;
  text-underline-position: under;
}
```

The initial value is `auto`, which lets the user agent choose the underline’s position. The `under` value asks for the underline to be placed beneath the text content, generally keeping it away from descenders such as those in “g”, “p”, and “y”.

This is especially helpful when underlines would otherwise run through glyphs and reduce readability. It can improve the appearance of links in body text, headings, and typefaces whose default underline metrics produce a line that sits too close to the letters. It is also useful for text containing subscripts, mathematical notation, or other characters that extend below the baseline.

The specification also defines `left` and `right` for choosing the side of the text in vertical writing modes. These keywords can be combined with `under` to provide appropriate positioning when content may use both horizontal and vertical writing modes.

There are a few caveats. Underline positioning depends on fonts, glyphs, writing mode, and other text-decoration properties, so `under` will not look identical in every design. A lower underline can also appear crowded when line spacing is very tight; text decorations do not reserve extra layout space. Test the result with your actual fonts, language content, and line-height.

Implementation details can differ between browser engines, particularly for vertical text or combinations of values. Check the browsers relevant to your project rather than assuming every value behaves identically. Where the declaration is unsupported, it is ignored and the browser’s normal underline positioning remains a reasonable fallback.

Further reading: [CSS Text Decoration Module Level 4 — `text-underline-position`](https://drafts.csswg.org/css-text-decor-4/#text-underline-position-property)
