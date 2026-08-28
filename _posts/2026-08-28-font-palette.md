---
title: "font-palette"
date: 2026-08-28
categories: ["CSS"]
tags: ["font-palette"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-palette-prop"
---

Color fonts can contain multiple built-in color palettes. The `font-palette` property selects which palette a browser should use when rendering text from such a font. This makes it possible to adapt icons, emoji, or decorative typography to a theme without swapping font files or recreating the artwork with SVG.

`font-palette` is defined in the CSS Fonts Module Level 4 specification. That specification is still a CSS Working Group draft rather than a finalized Recommendation, so details may continue to evolve.

The property can select the font’s normal palette, request a palette designed for light or dark backgrounds, or reference a custom palette created with `@font-palette-values`:

```css
@font-palette-values --brand {
  font-family: "Brand Color Font";
  base-palette: 0;
  override-colors:
    0 #0057b8,
    1 #ffd700;
}

.logo {
  font-family: "Brand Color Font";
  font-palette: --brand;
}
```

Here, `base-palette` selects one of the font’s existing palettes. `override-colors` replaces individual entries, identified by their font-specific color indexes. The custom palette name is a dashed identifier, such as `--brand`, which is then assigned through `font-palette`.

For simpler theme adaptation, you can use `light` or `dark`:

```css
.dark-theme .icon {
  font-palette: dark;
}
```

These keywords ask the browser to choose a palette intended for the corresponding background. The actual result depends on the palettes and metadata provided by the font.

This feature is useful today for sites using palette-capable color fonts. A single font can support light and dark themes, seasonal treatments, product branding, or state variations while retaining selectable, scalable text. Because `font-palette` is inherited, a palette can also be applied at a container level when several descendants use the same color font.

There are important caveats. The property has no useful effect on ordinary monochrome fonts or color fonts without applicable palette data. Custom overrides require knowledge of the font’s palette indexes, which are not standardized across fonts. The requested `light` or `dark` palette may also be unavailable or may look different from what you expect.

Browser support is not universal, so test in the browsers relevant to your audience and provide an acceptable default rendering. Also treat palette choices as visual styling rather than the sole way to communicate meaning or state.

Further reading: [CSS Fonts Module Level 4: `font-palette`](https://drafts.csswg.org/css-fonts-4/#font-palette-prop)
