---
title: "font-variant-alternates"
date: 2026-10-13
categories: ["CSS"]
tags: ["font-variant-alternates"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-variant-alternates-prop"
---

`font-variant-alternates` selects alternate glyphs supplied by a font without changing the underlying text. It can enable historical forms, stylistic alternatives, swashes, ornaments, annotations, stylistic sets, and character variants.

The property is defined in CSS Fonts Module Level 4. The linked specification is an Editor’s Draft, so it is standards-track work but may still change. There is no need to assign it a precise introduction date.

A minimal example uses `historical-forms`, which does not require additional CSS definitions:

```css
.archival-text {
  font-family: "Example Serif", serif;
  font-variant-alternates: historical-forms;
}
```

If the selected font contains the relevant historical glyph substitutions, the browser can use them for `.archival-text`. If it does not, the declaration may produce no visible change. Text selection, copying, searching, and assistive technologies still operate on the original characters because this is glyph substitution, not content replacement.

The property’s initial value is `normal`. Its other specified forms are `historical-forms` and the `stylistic()`, `styleset()`, `character-variant()`, `swash()`, `ornaments()`, and `annotation()` functions. These functions use named feature values associated with a font family through `@font-feature-values`. This indirection lets CSS use meaningful names instead of embedding font-specific numeric feature indexes throughout a stylesheet.

That makes `font-variant-alternates` useful for typography that is both expressive and maintainable. A design system can give an alternate a semantic name and map that name appropriately for each font family. It is generally clearer than reaching immediately for low-level `font-feature-settings`, while allowing fallback fonts to remain usable.

There are important caveats. First, the font must actually provide the requested alternate glyphs and OpenType features. Different fonts can expose very different sets of alternatives. Second, browser implementation may be incomplete or inconsistent, particularly for the functional values and their interaction with `@font-feature-values`; test the exact fonts, values, and target browsers your project uses rather than assuming uniform support. Finally, alternates can affect spacing, readability, and visual tone, so they should be treated as progressive typographic enhancement rather than required for understanding the content.

Further reading: [CSS Fonts Module Level 4 — `font-variant-alternates`](https://drafts.csswg.org/css-fonts-4/#font-variant-alternates-prop)
