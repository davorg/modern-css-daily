---
title: "font-variant-numeric"
date: 2026-09-29
categories: ["CSS"]
tags: ["font-variant-numeric"]
layout: single
source: "https://www.w3.org/TR/css-fonts-4/#font-variant-numeric-prop"
---

`font-variant-numeric` controls which alternate glyphs a font uses for numbers, punctuation, and fractions. It lets developers request typographic forms such as fixed-width digits, old-style numerals, slashed zeros, or specially designed fractions—without changing the underlying text.

The property is defined in the W3C’s CSS Fonts Module Level 4 standards work. It is a standard CSS property, not a browser-specific extension, though the visible result depends on the selected font and its available glyphs.

A common use is aligning numbers in tables:

```css
.financial-data {
  font-variant-numeric: lining-nums tabular-nums;
}
```

`lining-nums` requests numerals designed to sit at a consistent height, while `tabular-nums` requests equal-width digits. Together, they make columns of prices, measurements, or statistics easier to scan.

The specification defines several categories of values:

- `lining-nums` and `oldstyle-nums` select numeral shapes.
- `proportional-nums` and `tabular-nums` control numeral spacing.
- `diagonal-fractions` and `stacked-fractions` request fraction forms.
- `ordinal` enables special forms for ordinal markers.
- `slashed-zero` distinguishes zero from letters such as uppercase “O”.
- `normal` disables the alternate numeric forms selected by this property.

Compatible values from different categories can be combined in one declaration. For example:

```css
.report {
  font-variant-numeric: oldstyle-nums proportional-nums;
}
```

This feature is useful today because numerical typography affects both readability and layout. Tabular numerals prevent changing values from shifting horizontally in dashboards, counters, timers, and data tables. Old-style or proportional numerals can blend more naturally into running prose. A slashed zero can improve clarity in technical identifiers.

There are important caveats. CSS requests these forms, but fonts supply them. If the chosen font lacks the corresponding glyphs or font feature, the declaration may produce no visible change. Results can also vary when font fallback causes different characters to come from different fonts. Test with the actual font files and content used by your site.

Do not rely on these values to change the meaning of text or perform formatting. They affect glyph selection, not the document’s characters, numeric precision, localization, or accessibility semantics.

Further reading: [CSS Fonts Module Level 4: `font-variant-numeric`](https://www.w3.org/TR/css-fonts-4/#font-variant-numeric-prop)
