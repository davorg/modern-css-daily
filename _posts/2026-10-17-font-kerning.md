---
title: "font-kerning"
date: 2026-10-17
categories: ["CSS"]
tags: ["font-kerning"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-kerning-prop"
---

Kerning adjusts the spacing between particular pairs of glyphs. For example, combinations such as “AV” or “To” may look too far apart when each character uses only its standard advance width. A font can provide kerning data that moves those glyphs closer together—or occasionally farther apart—for more visually balanced text.

CSS exposes this behavior through the `font-kerning` property:

```css
.headline {
  font-kerning: normal;
}
```

The property accepts three values:

- `auto`: lets the user agent decide whether to apply kerning, potentially using contextual factors such as text size or rendering performance.
- `normal`: requests that kerning be applied.
- `none`: requests that kerning not be applied.

The initial value is `auto`, and the property is inherited. Setting it on a container can therefore affect all descendant text unless another rule overrides it.

`font-kerning` is defined in CSS Fonts Module Level 4. That module is a CSS Working Group draft rather than a finalized W3C Recommendation, so details may still be refined. The feature should be treated as a standards-defined enhancement whose real-world behavior must be tested in the browsers and rendering environments your project supports.

Why use it today? Good kerning can make headings, logos, navigation labels, and other prominent text appear more polished without manually adjusting letter spacing. `font-kerning: normal` is especially useful when consistent use of a font’s kerning information matters more than leaving the decision to the browser. Conversely, `none` can help when evaluating type metrics or when a design intentionally requires unkerned spacing.

There are important caveats. The visual result depends on the selected font: if the font provides no useful kerning data for a particular pair, enabling kerning may produce no visible change. Results may also differ across fonts, scripts, shaping engines, and user agents. Kerning is pair-specific, so it is not a substitute for `letter-spacing`, which applies broader tracking adjustments.

Browser implementation should not be assumed solely from the presence of the property. Test representative text with your actual fonts, including fallback fonts and variable font configurations where applicable. Kerning can improve typography, but it should remain a progressive enhancement rather than a requirement for readable or correctly laid-out content.

Further reading: [CSS Fonts Module Level 4 — `font-kerning`](https://drafts.csswg.org/css-fonts-4/#font-kerning-prop)
