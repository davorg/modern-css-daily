---
title: "ruby-position"
date: 2026-10-08
categories: ["CSS"]
tags: ["ruby-position"]
layout: single
source: "https://www.w3.org/TR/css-ruby-1/#rubypos"
---

`ruby-position` controls where ruby annotations are placed relative to their base text. Ruby is commonly used in East Asian typography for pronunciation guides, readings, or short glosses—for example, Japanese furigana above kanji.

The property is defined by CSS Ruby Annotation Layout Module Level 1. The cited W3C document is a Working Draft rather than a final W3C Recommendation, so details may still be refined.

A minimal example uses semantic HTML ruby elements and places the annotation on the line-over side of the base text:

```html
<ruby class="reading">
  漢字<rt>かんじ</rt>
</ruby>
```

```css
.reading {
  ruby-position: over;
}
```

In horizontal writing, `over` places the annotation above the base. In vertical writing, it places it on the corresponding line-over side. The property applies to ruby annotation containers and is inherited, so setting it on the `<ruby>` element allows the generated annotation container to receive the value.

The specification also defines `under`, which selects the line-under side; `alternate`, which alternates sides when there are multiple annotation levels; and `inter-character`, which supports annotations positioned between characters. These values address layouts found in real publishing traditions rather than treating ruby as ordinary superscript text.

This is useful today because native ruby layout understands the relationship between the base and its annotation. Browsers can account for annotation sizing, alignment, writing direction, and line spacing more appropriately than hand-built layouts using positioned `<span>` elements. It also keeps the HTML meaningful: `<ruby>` identifies the annotated text, while `<rt>` identifies its annotation. CSS then controls presentation without changing that structure.

There are caveats. The module remains a Working Draft, and implementation coverage and behavior may differ among browsers, particularly for less common values, nested annotation levels, and complex vertical layouts. Font metrics can also affect spacing and visual alignment. Test the exact combinations of `ruby-position`, `writing-mode`, language, fonts, and markup that your project uses.

Use ruby markup for semantics first, then treat explicit positioning as a progressive enhancement. Avoid replacing the annotation relationship with visual-only positioning, since that can produce fragile line layout and less useful document structure.

Further reading: [CSS Ruby Annotation Layout Module Level 1 — Ruby Positioning](https://www.w3.org/TR/css-ruby-1/#rubypos)
