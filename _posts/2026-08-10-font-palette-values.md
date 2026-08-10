---
title: "@font-palette-values"
date: 2026-08-10
categories: ["CSS"]
tags: ["@font-palette-values"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-palette-values"
---

`@font-palette-values` lets CSS authors define a custom color palette for a color font. The palette can then be selected with the `font-palette` property.

The feature is defined in CSS Fonts Module Level 4. That specification remains a draft, so details may still change and implementations may not be consistent across browsers.

A custom palette starts from one of the palettes embedded in the font. Individual color entries can then be replaced by referring to their numeric palette indexes:

```css
@font-palette-values --brand {
  font-family: "Example Color Font";
  base-palette: 0;
  override-colors:
    0 #0057b8,
    1 #ffd700;
}

.logo {
  font-family: "Example Color Font";
  font-palette: --brand;
}
```

Here, `--brand` is the palette’s custom name. The `font-family` descriptor associates it with a particular font family. `base-palette: 0` selects an existing palette from that font, while `override-colors` replaces entries 0 and 1.

The exact meaning of those indexes depends on the font. CSS does not assign semantic roles such as “foreground” or “accent” to palette entries; the font’s palette data determines which glyph layers use each color. Developers therefore need documentation for the chosen font or must inspect its palette structure.

This feature is useful for adapting a single color-font asset to different brands, themes, or interface states. Instead of downloading separate font files for light and dark themes—or editing the font itself—you can define multiple named palettes in CSS and select the appropriate one through `font-palette`. It can also keep typography aligned with a site’s design system while preserving the layered detail of color glyphs.

There are important caveats. The font must contain compatible color and palette information; `@font-palette-values` does not turn an ordinary monochrome font into a color font. Palette numbers and color-entry indexes are font-specific, and an incorrect index will not produce the intended design. Browser support should also be verified for the environments you target rather than assumed. In browsers that do not understand the at-rule or `font-palette`, the custom palette will not be applied, so designs should remain readable with the font’s default rendering or another fallback font.

### Further reading

[CSS Fonts Module Level 4: `@font-palette-values`](https://drafts.csswg.org/css-fonts-4/#font-palette-values)
