---
title: "light-dark()"
date: 2026-08-09
categories: ["CSS"]
tags: ["light-dark()"]
layout: single
source: "https://drafts.csswg.org/css-color-5/#light-dark"
---

The CSS `light-dark()` color function lets you provide two colors for a property: one for a light color scheme and one for a dark color scheme. The browser selects between them according to the element’s **used color scheme**.

The function is defined in CSS Color Module Level 5, which remains a draft rather than a finalized W3C Recommendation. Implementations may therefore vary, so check current browser documentation and test your target environments.

A minimal example looks like this:

```css
:root {
  color-scheme: light dark;
}

body {
  color: light-dark(#222, #eee);
  background-color: light-dark(#fff, #121212);
}
```

The current syntax is:

```css
light-dark(<color>, <color>)
```

The first argument is the color for a light scheme; the second is for a dark scheme.

Declaring `color-scheme: light dark` is important. It tells the browser that the element supports both schemes, allowing the browser to establish the used color scheme from the user’s preferences and other relevant settings. Without appropriate `color-scheme` configuration, `light-dark()` may not switch as expected.

The main benefit is locality. Instead of putting related color declarations in separate `prefers-color-scheme` media-query blocks, you can keep both alternatives next to the property they affect. This is particularly convenient for design tokens:

```css
:root {
  color-scheme: light dark;
  --surface: light-dark(white, #181818);
  --text: light-dark(#202020, #f2f2f2);
}

.card {
  color: var(--text);
  background: var(--surface);
}
```

There are several caveats. Browsers that do not understand the function will reject that declaration, so consider a conventional fallback placed first:

```css
.card {
  background-color: white;
  background-color: light-dark(white, #181818);
}
```

That fallback provides a usable default, but it does not recreate automatic dark-mode behavior in unsupported browsers.

Also, `light-dark()` only chooses between colors. It does not guarantee sufficient contrast, account for every accessibility mode, or replace thoughtful testing. Verify both variants against surrounding colors and test user-agent features such as forced-color modes separately. Finally, remember that selection is based on the used color scheme, not directly on whether a particular media query matches.

Further reading: [CSS Color Module Level 5 — `light-dark()`](https://drafts.csswg.org/css-color-5/#light-dark)
