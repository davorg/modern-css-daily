---
title: "font-feature-settings"
date: 2026-10-18
categories: ["CSS"]
tags: ["font-feature-settings"]
layout: single
source: "https://www.w3.org/TR/css-fonts-4/#font-feature-settings-prop"
---

`font-feature-settings` provides low-level control over typographic features built into OpenType fonts. It lets developers enable or disable features by their four-character OpenType tags, such as stylistic sets, alternate glyphs, or specialized number forms.

The property is defined by the W3C in CSS Fonts Module Level 4. It is standard CSS rather than a vendor-specific extension, although the availability and visual effect of any particular feature depend on the selected font.

A minimal example enables the font’s first stylistic set:

```css
.callout {
  font-feature-settings: "ss01" on;
}
```

If the active font includes the `ss01` feature, text inside `.callout` may use alternate glyph designs supplied by that feature. If the font does not provide it, enabling the tag has no visible effect.

Multiple settings can be supplied as a comma-separated list:

```css
.invoice-total {
  font-feature-settings: "tnum" on, "zero" on;
}
```

Feature values may use `on`, `off`, or a non-negative integer. Omitting the value is equivalent to enabling the feature with a value of `1`. Feature tags are case-sensitive.

This property remains useful when a font exposes capabilities that do not have a convenient high-level CSS equivalent. It is particularly valuable for design systems, editorial layouts, branding, and interfaces that need precise access to a typeface’s stylistic sets or custom OpenType behavior.

However, `font-feature-settings` should not be the first choice for common typography. Prefer higher-level properties such as `font-variant-ligatures`, `font-variant-numeric`, `font-variant-caps`, or `font-kerning` when they express the intended result. Those properties describe typographic intent more clearly and allow user agents to apply appropriate behavior across fonts.

There are also practical caveats. OpenType tags are font-specific: enabling a feature does not guarantee that the current font supports it or that different fonts implement it identically. A fallback font may produce different results or none at all. Developers should test with the actual font stack, scripts, languages, and content being shipped. Avoid assuming that an unfamiliar tag is valid or meaningful simply because another font recognizes it.

Further reading: [CSS Fonts Module Level 4 — `font-feature-settings`](https://www.w3.org/TR/css-fonts-4/#font-feature-settings-prop)
