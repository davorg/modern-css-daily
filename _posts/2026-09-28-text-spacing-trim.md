---
title: "text-spacing-trim"
date: 2026-09-28
categories: ["CSS"]
tags: ["text-spacing-trim"]
layout: single
source: "https://drafts.csswg.org/css-text-4/#text-spacing-trim-property"
---

`text-spacing-trim` controls spacing around full-width punctuation, primarily for Chinese, Japanese, and Korean typography. Characters such as brackets, commas, and full stops often include space within their full-width advance. Depending on where they occur, that space can produce an unwanted gap at a line edge or excessive spacing when punctuation marks are adjacent.

The property lets the browser adjust that spacing according to CJK typographic conventions. Unlike manually inserted spaces, negative margins, or script-based fixes, it operates during text layout. That matters because punctuation can move to the start or end of a line whenever the viewport, font, or content changes.

For example, the `trim-start` value trims the spacing of eligible opening punctuation at the start of a line:

```css
:lang(ja),
:lang(zh) {
  text-spacing-trim: trim-start;
}
```

Using language selectors is a good practice because punctuation conventions depend on the content’s writing system and language. Documents should also carry accurate `lang` attributes—for example, `<article lang="ja">`—rather than relying only on visual appearance.

This feature is useful today for responsive articles, documentation, captions, and interfaces containing CJK text. It allows line wrapping to remain fluid while avoiding brittle markup changes. It also preserves the underlying characters, so copying, searching, accessibility APIs, and text processing do not receive punctuation modified solely for presentation.

`text-spacing-trim` is defined in CSS Text Module Level 4. That module is still a CSS Working Group draft rather than a finalized W3C Recommendation, so details may continue to evolve.

Browser support should be treated as a progressive enhancement. Availability and completeness can differ between implementations; check current compatibility information and test with the fonts, languages, writing modes, and line-breaking situations your project uses. Unsupported browsers will ignore the declaration and retain their normal punctuation spacing. The result can therefore differ visually without making the text unreadable.

The property is not a general-purpose whitespace-removal tool. It does not replace correct punctuation, language metadata, or ordinary CSS layout, and its effects are limited to the punctuation and contexts defined by the specification. Avoid compensating for unsupported behavior with inserted spaces or punctuation-specific markup unless the editorial design truly requires a fixed result.

Further reading: [CSS Text Module Level 4 — `text-spacing-trim`](https://drafts.csswg.org/css-text-4/#text-spacing-trim-property)
