---
title: "font-variant-ligatures"
date: 2026-10-03
categories: ["CSS"]
tags: ["font-variant-ligatures"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-variant-ligatures-prop"
---

`font-variant-ligatures` controls which ligatures and contextual forms a browser may use when shaping text. Ligatures replace character sequences—such as “fi”—with a single, specially designed glyph. Contextual forms select glyphs based on surrounding characters.

The property is defined in CSS Fonts Module Level 4, part of the CSS standards process. The linked specification is an Editor’s Draft, so details may continue to evolve; avoid assuming that every implementation handles every font and writing system identically.

A minimal example:

```css
.prose {
  font-variant-ligatures: common-ligatures contextual;
}

.code {
  font-variant-ligatures: none;
}
```

The first rule explicitly enables common ligatures and contextual forms. The second disables the optional ligature and contextual categories controlled by this property, which can make character sequences easier to distinguish in source code, identifiers, or other text where exact character recognition matters.

The initial value is `normal`. Under normal behavior, common ligatures and contextual forms are generally enabled, while discretionary and historical ligatures are not. Authors can control four categories using the paired keywords `common-ligatures` and `no-common-ligatures`, `discretionary-ligatures` and `no-discretionary-ligatures`, `historical-ligatures` and `no-historical-ligatures`, and `contextual` and `no-contextual`. Multiple compatible keywords can be combined in one declaration.

This feature is useful today because it exposes typographic choices without requiring alternate font files or direct use of lower-level font feature settings. Editorial sites can enable discretionary ligatures for display text, historical material can request historical forms, and technical interfaces can disable optional substitutions where visual ambiguity is undesirable. The property is inherited, so it can also be applied efficiently to a document section.

There are important caveats. CSS can request a feature, but it cannot create glyphs or substitutions that the selected font does not provide. Results therefore depend on the font, text, language, script, and shaping engine. Some scripts also require shaping behavior for correct rendering; this property should not be treated as a way to bypass required text shaping. Ligatures can affect visual appearance and cursor behavior, so test editable text and interfaces carefully.

Finally, do not infer support from the presence of a font feature alone. Test the property with your actual fonts and target browsers, and provide readable output when a requested substitution has no visible effect.

**Further reading:** [CSS Fonts Module Level 4: `font-variant-ligatures`](https://drafts.csswg.org/css-fonts-4/#font-variant-ligatures-prop)
