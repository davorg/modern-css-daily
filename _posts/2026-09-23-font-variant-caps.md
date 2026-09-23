---
title: "font-variant-caps"
date: 2026-09-23
categories: ["CSS"]
tags: ["font-variant-caps"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-variant-caps-prop"
---

`font-variant-caps` controls the use of typographic alternatives for capital letters. It lets authors request true small capitals, petite capitals, unicase forms, or capitals designed specifically for headings—without changing the text itself.

The property is defined in CSS Fonts Module Level 4, currently published as an Editor’s Draft. It builds on font features supplied by the selected typeface, commonly through corresponding OpenType features. The specification may continue to evolve, so consult it when relying on detailed behavior.

A minimal example:

```css
.abbreviation {
  font-variant-caps: small-caps;
}
```

```html
<p>The <abbr class="abbreviation">CSS</abbr> specification is evolving.</p>
```

The current property values are `normal`, `small-caps`, `all-small-caps`, `petite-caps`, `all-petite-caps`, `unicase`, and `titling-caps`.

`small-caps` uses small-cap glyphs for lowercase letters while retaining regular capitals. `all-small-caps` requests small-cap forms for both uppercase and lowercase letters. Petite-cap variants work similarly but request petite capitals, which may differ in size and design. `unicase` requests a mixed-case design, while `titling-caps` selects capital forms intended for display text such as headings.

This is useful today because it separates content from presentation. Authors sometimes imitate small caps by converting text to uppercase and reducing its font size. That approach can produce inferior spacing and weight, and it alters—or requires duplicating—the text’s casing. `font-variant-caps` instead preserves the source text and asks the font for purpose-designed glyphs.

The main caveat is font support. A typeface must contain the relevant glyphs and font features for the requested result to appear as designed. Depending on the value, font, and user-agent behavior, the browser may use fallback behavior or synthesized forms rather than true designed capitals. Synthetic small caps can look noticeably different from authentic glyphs.

Implementation support may also vary by value and rendering environment, so test with the actual browsers, operating systems, and fonts used by your project. Include an appropriate fallback font, and treat these variants as typographic enhancement rather than something required to understand the content.

Further reading: [CSS Fonts Module Level 4: `font-variant-caps`](https://drafts.csswg.org/css-fonts-4/#font-variant-caps-prop)
