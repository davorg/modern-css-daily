---
title: "@counter-style"
date: 2026-08-13
categories: ["CSS"]
tags: ["@counter-style"]
layout: single
source: "https://drafts.csswg.org/css-counter-styles-3/#the-counter-style-rule"
---

`@counter-style` lets you define a named numbering or marker system for lists and CSS counters. Instead of relying only on built-in styles such as `decimal`, `lower-roman`, or `disc`, you can create styles based on symbols, alphabetic sequences, numeric systems, or additive numbering rules.

The feature is defined in CSS Counter Styles Level 3, a standards-track specification maintained by the CSS Working Group. The linked specification is the current draft, so details may still be refined; it should not be treated as an immutable, finalized standard.

A minimal custom marker style looks like this:

```css
@counter-style checkmarks {
  system: cyclic;
  symbols: "✓";
  suffix: " ";
}

.tasks {
  list-style-type: checkmarks;
}
```

```html
<ul class="tasks">
  <li>Write tests</li>
  <li>Review the documentation</li>
  <li>Deploy the release</li>
</ul>
```

Here, `system: cyclic` tells the browser to cycle through the values supplied by `symbols`. Because there is only one symbol, every list item receives the same checkmark. `suffix` inserts a space after the marker.

More sophisticated styles can use descriptors defined by the specification, including `negative`, `prefix`, `range`, `pad`, `fallback`, and `speak-as`. The `system` descriptor selects how symbols are interpreted—for example, as a cyclic set, a fixed sequence, an alphabetic system, a numeric system, or an additive system.

This is useful for localized numbering systems, culturally appropriate list markers, publication and legal-document conventions, and reusable visual markers. Defining the behavior once in an at-rule is generally clearer and easier to maintain than manually inserting marker text into every list item. It also preserves the document’s list structure instead of turning markers into content.

There are caveats. Browser support can vary across the at-rule’s descriptors and rendering contexts, so test the specific systems and descriptors you use in your target browsers. Also check printing, generated content, font availability, and accessibility behavior. In particular, a visual symbol may not have an obvious spoken equivalent. Unsupported or invalid custom counter styles can fall back according to the specification, so do not use a marker as the only way to communicate essential information.

Further reading: [CSS Counter Styles Level 3 — The `@counter-style` rule](https://drafts.csswg.org/css-counter-styles-3/#the-counter-style-rule)
