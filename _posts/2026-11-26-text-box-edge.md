---
title: "text-box-edge"
date: 2026-11-26
categories: ["CSS"]
tags: ["text-box-edge"]
layout: single
source: "https://drafts.csswg.org/css-inline-3/#propdef-text-box-edge"
---

`text-box-edge` lets authors choose which font metrics define the upper and lower edges of a text box. Used with `text-box-trim`, it can remove the extra leading that browsers normally preserve above and below inline text.

This is useful because a line box is usually based on `line-height`, not the visible bounds of its letters. A heading may therefore appear to have unexplained space above its capital letters, while text inside a button can look vertically off-center even when its padding is mathematically equal.

A minimal example is:

```css
.button-label {
  line-height: 1.4;
  text-box-trim: trim-both;
  text-box-edge: cap alphabetic;
}
```

Here, `text-box-trim: trim-both` trims both sides of the text box. `text-box-edge: cap alphabetic` selects the font’s cap-height edge for the line-over side and its alphabetic baseline for the line-under side. The result is a box whose dimensions correspond more closely to capital-letter text rather than the full line-height area.

The property accepts one or two edge keywords. When two are supplied, the first controls the line-over edge and the second controls the line-under edge. The specification also defines edges based on text, x-height, ideographic metrics, and ink bounds. These choices make the feature applicable to more than Latin uppercase labels.

Today, `text-box-edge` can make component spacing more predictable. It is especially relevant to buttons, badges, navigation labels, display headings, and other elements where visible glyph alignment matters. It can replace brittle techniques such as font-specific negative margins, transformed text, or manually adjusted padding. Because it uses font metrics, it can also adapt better when a font changes.

There are important caveats. `text-box-edge` is defined in the Editor’s Draft of CSS Inline Layout Module Level 3; it is not yet a finalized CSS Recommendation, and implementations may be incomplete or inconsistent. Check current compatibility for your target browsers rather than assuming support. Unsupported declarations are ignored, so retain sensible `line-height` and padding as the fallback.

Trimming changes layout measurements; it does not crop glyphs. Accents, descenders, or decorative glyphs can extend beyond the selected edge, so test with the actual fonts, languages, and content your interface uses. Ink-based edges can also vary with the rendered text, which may be undesirable when components need uniform dimensions.

Further reading: [CSS Inline Layout Module Level 3 — `text-box-edge`](https://drafts.csswg.org/css-inline-3/#propdef-text-box-edge)
