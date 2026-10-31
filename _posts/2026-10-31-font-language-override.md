---
title: "font-language-override"
date: 2026-10-31
categories: ["CSS"]
tags: ["font-language-override"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#propdef-font-language-override"
---

`font-language-override` controls which language system a font uses during text shaping. OpenType fonts can contain language-specific substitutions and positioning—for example, alternative glyph forms for Serbian Cyrillic or regional forms of Han characters. Browsers normally infer the appropriate font language system from the content language, such as an HTML `lang` attribute. This property lets CSS override that choice.

The property is defined in CSS Fonts Module Level 4, which is currently a CSS Working Group Editor’s Draft. Its presence in a draft specification does not guarantee consistent implementation across browsers, so test it in the environments you support.

The current syntax accepts either `normal` or a string identifying an OpenType language system:

```css
.serbian-glyphs {
  font-language-override: "SRB";
}
```

With `"SRB"`, the browser asks the selected font to use its Serbian language system when shaping the element’s text. The initial value, `normal`, applies no override and leaves language selection to the browser’s normal inference.

This is useful when the language associated with the content does not produce the desired OpenType behavior, or when a particular font organizes its language-specific forms in a way that requires an explicit language-system selection. It can also help with tightly controlled typography where authors know exactly which language-specific glyph forms a chosen font provides.

The string is an OpenType language-system tag, not a general-purpose language identifier such as a BCP 47 tag. Do not use this property as a substitute for correct HTML language metadata. Keep `lang` accurate for accessibility tools, pronunciation, spell-checking, hyphenation, and other language-sensitive behavior; use `font-language-override` only to influence font shaping.

There are several practical caveats. The selected font must actually contain relevant language-specific OpenType behavior. If it does not support the requested language system, the override may have no visible effect. Results can also depend on the browser’s font and text-shaping implementation. Browsers that do not support the property will ignore the declaration and continue with their normal language inference. Test with the exact fonts, scripts, operating systems, and browsers used by your audience rather than assuming that a valid declaration will visibly change every font.

Further reading: [CSS Fonts Module Level 4 — `font-language-override`](https://drafts.csswg.org/css-fonts-4/#propdef-font-language-override)
