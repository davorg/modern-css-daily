---
title: "text-underline-offset"
date: 2026-08-07
categories: ["CSS"]
tags: ["text-underline-offset"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-underline-offset-property"
---

`text-underline-offset` controls the distance between underlined text and its underline. Positive values move the underline away from the text, while negative values move it toward the text. This works independently of the declaration that creates the underline.

The property is defined in CSS Text Decoration Module Level 4. The cited specification is an Editor’s Draft, so details may continue to evolve rather than representing a finalized W3C Recommendation.

A minimal example looks like this:

```css
a {
  text-decoration-line: underline;
  text-underline-offset: 0.2em;
}
```

The property accepts `auto`, a length, or a percentage. With `auto`, the browser chooses the offset. Relative values such as `em` can help the spacing feel proportional to the surrounding type. Percentages are relative to the element’s font size.

This small typographic control is useful because default underline placement does not always suit every font, size, or design. An underline may sit too close to letterforms, making links look crowded or causing the line to meet glyphs with descenders. A modest offset can improve clarity while preserving the familiar visual cue that text is a link.

It is also helpful in design systems. Instead of replacing underlines with borders, backgrounds, or positioned pseudo-elements, developers can keep the browser’s native text decoration and adjust its placement directly. That generally produces simpler CSS and continues to work when text wraps across multiple lines.

There are several caveats. `text-underline-offset` does not create an underline; pair it with `text-decoration-line: underline` or another rule that already applies one. It affects underlines, not overlines or line-through decorations. The property is inherited, so a value set on a container may influence underlined descendants.

The final appearance can vary with the font, writing mode, browser-chosen default underline position, and other text-decoration properties. Large positive or negative offsets can also create visual collisions with adjacent lines or the text itself, so test with representative content and fonts.

Support should be checked against the browsers and rendering environments required by your project rather than assumed from a specific version or percentage. Where the declaration is unsupported, it is ignored and the underline uses its normal placement, making the default behavior a reasonable fallback.

Further reading: [CSS Text Decoration Module Level 4: `text-underline-offset`](https://drafts.csswg.org/css-text-decor-4/#text-underline-offset-property)
