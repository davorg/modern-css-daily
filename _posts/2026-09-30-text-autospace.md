---
title: "text-autospace"
date: 2026-09-30
categories: ["CSS"]
tags: ["text-autospace"]
layout: single
source: "https://drafts.csswg.org/css-text-4/#text-autospace-property"
---

`text-autospace` controls typographic spacing at boundaries between ideographic text—such as Chinese or Japanese—and adjacent non-ideographic letters or numbers. For example, it can separate a Han character from `CSS` or `2026` without requiring literal spaces in the HTML.

The property is defined in the draft CSS Text Module Level 4 specification. Because the module remains a draft, its details may still evolve. Browser implementation is not universal, so it should currently be treated as a progressive enhancement rather than a layout requirement.

A minimal example using the current syntax is:

```html
<p class="mixed-text" lang="zh">学习CSS2规范</p>
```

```css
.mixed-text {
  text-autospace: ideograph-alpha ideograph-numeric;
}
```

Here, `ideograph-alpha` requests spacing between ideographic characters and non-ideographic letters. `ideograph-numeric` does the same for adjacent numerals. The two keywords can be combined in one declaration.

The property is useful because mixed-script typography often needs spacing that is not represented by ordinary word boundaries. Authors have traditionally handled this by inserting spaces manually, wrapping script transitions in elements, or relying on language-specific typesetting code. Those approaches complicate templates and are particularly awkward when text comes from a CMS, localization system, or user input.

With `text-autospace`, the text remains free of author-inserted whitespace while the browser handles the visual spacing. The property is inherited, so it can usually be applied to a document section instead of every individual text run.

There are important caveats. Unsupported browsers will ignore the declaration, leaving characters directly adjacent unless some other styling or source whitespace separates them. Do not depend on automatic spacing to prevent overlap or satisfy fixed measurements. Test mixed-script content in the browsers and fonts relevant to your users, especially when line wrapping or narrow containers matter.

The specification also provides `normal`, which uses the user agent’s normal automatic-spacing behavior, and `no-autospace`, which disables such spacing. Prefer explicit values when a particular distinction between letters and numbers is important. A feature query such as `@supports (text-autospace: ideograph-alpha)` can be used when additional fallback styling is necessary.

Further reading: [CSS Text Module Level 4 — `text-autospace`](https://drafts.csswg.org/css-text-4/#text-autospace-property)
