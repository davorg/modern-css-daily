---
title: "contrast-color()"
date: 2026-09-16
categories: ["CSS"]
tags: ["contrast-color()"]
layout: single
source: "https://drafts.csswg.org/css-color-6/#contrast-color"
---

`contrast-color()` automatically chooses a readable foreground color for a given color. It accepts one `<color>` argument and resolves to either black or white, whichever provides greater contrast with that color. A common use is selecting text color for buttons, badges, or cards whose backgrounds vary.

The function is defined in CSS Color Module Level 6. That module is currently a CSS Working Group Editor’s Draft, not a finalized standard, so details may still change. Browser availability may also vary; check compatibility for your project’s supported browsers.

The current syntax is simply `contrast-color(<color>)`:

```css
.button {
  --button-background: #0b57d0;

  background-color: var(--button-background);
  color: white;
  color: contrast-color(var(--button-background));
}
```

The first `color` declaration is a fallback. Browsers that understand `contrast-color()` use the second declaration; browsers that do not will discard it and retain `white`.

This is especially useful for reusable components and design systems. A button might receive its background from a theme, a custom property, or user-selected data. Without `contrast-color()`, developers often need JavaScript, precomputed foreground/background pairs, or manually maintained classes. Because this function participates in normal CSS value resolution, it can respond directly when a custom property changes.

There are important limits. The function returns only black or white; it does not choose from a brand palette or produce a tinted complementary color. It also evaluates the color passed as its argument. It does not inspect the element’s rendered background, nearby content, gradients, background images, blending, overlays, or other pixels behind the text. Authors therefore need to pass the relevant background color explicitly.

Choosing the higher-contrast option is helpful, but it should not replace accessibility testing. The final result can still be affected by opacity, compositing, font size and weight, visual effects, and the actual rendered context. Projects must also consider focus indicators, borders, icons, and non-text contrast separately.

For now, treat `contrast-color()` as a progressive enhancement: provide a sensible fallback, test in target browsers, and verify the rendered component rather than assuming the function alone guarantees accessibility.

Further reading: [CSS Color Module Level 6 — `contrast-color()`](https://drafts.csswg.org/css-color-6/#contrast-color)
