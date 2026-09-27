---
title: "font-variant-position"
date: 2026-09-27
categories: ["CSS"]
tags: ["font-variant-position"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-variant-position-prop"
---

`font-variant-position` selects typographic subscript or superscript glyphs from a font. Rather than shrinking ordinary characters and moving them with `vertical-align`, it asks the font for purpose-designed alternatives, typically exposed through the OpenType `subs` and `sups` features.

The property accepts three values:

- `normal` — disables positional variants.
- `sub` — selects subscript variants.
- `super` — selects superscript variants.

It is defined in CSS Fonts Module Level 4, which is published as an Editor’s Draft. As with any draft specification, details and implementation behavior should be verified against current browsers rather than tied to an assumed introduction date.

A progressively enhanced example can preserve the normal HTML rendering when the property is not recognized:

```html
<p>Water is H<sub>2</sub>O, and 4 = 2<sup>2</sup>.</p>
```

```css
@supports (font-variant-position: sub) {
  sub,
  sup {
    font-size: inherit;
    vertical-align: baseline;
  }

  sub {
    font-variant-position: sub;
  }

  sup {
    font-variant-position: super;
  }
}
```

Resetting `font-size` and `vertical-align` is important here because browsers commonly style `<sub>` and `<sup>` by reducing and repositioning ordinary glyphs. Without that reset, the browser’s default styling could be combined with the font’s already-positioned variants.

This feature is useful for mathematical expressions, chemical formulas, footnote markers, ordinals, and other text where a typeface provides carefully drawn positional forms. Those glyphs can have better weight, spacing, and legibility than mechanically scaled text. The text baseline remains unchanged, so using them does not itself alter line-box layout. Semantic `<sub>` and `<sup>` elements can also remain in the markup instead of replacing meaning with purely visual spans.

There are caveats. Results depend heavily on the selected font: not every typeface contains suitable subscript or superscript glyphs for every character. The specification defines synthesized rendering when the needed variants are unavailable throughout a text run, but synthesized forms may not match the quality of designed glyphs. Font fallback, mixed scripts, and browser implementation differences can also affect results.

Treat `font-variant-position` as progressive typographic enhancement. Test with the actual fonts, characters, and target browsers used by your site, and retain semantic HTML or another acceptable fallback.

Further reading: [CSS Fonts Module Level 4 — `font-variant-position`](https://drafts.csswg.org/css-fonts-4/#font-variant-position-prop)
