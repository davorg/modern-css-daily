---
title: "font-variant-east-asian"
date: 2026-10-09
categories: ["CSS"]
tags: ["font-variant-east-asian"]
layout: single
source: "https://drafts.csswg.org/css-fonts/#font-variant-east-asian-prop"
---

`font-variant-east-asian` controls alternate glyph forms used in East Asian typography. It lets authors request glyph variants associated with particular Japanese standards, simplified or traditional forms, different character widths, and glyphs designed for ruby annotations.

The property is defined in CSS Fonts Module Level 4. The linked specification is a CSS Working Group Editor’s Draft, so it remains subject to revision; no particular introduction date should be inferred from that status.

A minimal example requests Japanese glyph forms corresponding to JIS 2004:

```html
<p lang="ja" class="jis-2004">日本語のテキスト</p>
```

```css
.jis-2004 {
  font-variant-east-asian: jis04;
}
```

The property accepts `normal` or values from three groups:

- Variant forms: `jis78`, `jis83`, `jis90`, `jis04`, `simplified`, or `traditional`
- Width forms: `full-width` or `proportional-width`
- Ruby forms: `ruby`

Compatible values from different groups can be combined:

```css
.annotation {
  font-variant-east-asian: traditional proportional-width ruby;
}
```

This is useful when typographic conventions matter independently of the underlying Unicode text. A Japanese publication can select glyph shapes associated with a particular JIS revision, while Chinese content can request simplified or traditional glyph variants where the font provides them. Width variants can help text fit a design while preserving the original characters. The `ruby` value requests glyphs intended for small annotation text, although it does not create ruby annotations or perform ruby layout by itself.

There are important caveats. The property selects alternate glyphs; it does not translate text, convert simplified Chinese characters to traditional characters, or replace one Unicode character with another. Its visible effect depends on the selected font containing and exposing the relevant typographic features. Font fallback may therefore produce inconsistent results across a run of text.

Authors should also set an appropriate `lang` attribute, because language information can affect font selection and glyph shaping beyond this property. Test with the actual fonts, scripts, and fallback stacks used by the site. Browser compatibility should likewise be checked for the environments you support rather than assumed from the specification alone.

**Further reading:** [CSS Fonts Module: `font-variant-east-asian`](https://drafts.csswg.org/css-fonts/#font-variant-east-asian-prop)
