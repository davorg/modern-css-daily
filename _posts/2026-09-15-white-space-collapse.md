---
title: "white-space-collapse"
date: 2026-09-15
categories: ["CSS"]
tags: ["white-space-collapse"]
layout: single
source: "https://drafts.csswg.org/css-text-4/#white-space-collapse-property"
---

`white-space-collapse` controls how an element handles spaces, tabs, and segment breaks—such as line breaks in source text. Its initial value is `collapse`, which produces the familiar HTML behavior of collapsing runs of whitespace. The property is inherited.

It is defined in CSS Text Module Level 4. That specification is still an evolving draft rather than a finalized W3C Recommendation, so details and implementation coverage may change.

A minimal example preserves source line breaks while continuing to collapse runs of spaces and tabs:

```html
<p class="message">First line
Second line</p>
```

```css
.message {
  white-space-collapse: preserve-breaks;
}
```

This renders the two pieces of text on separate lines without requiring a `<br>` element.

The specification defines these values:

- `collapse` collapses white-space sequences according to the normal collapsing rules.
- `discard` discards affected white-space characters.
- `preserve` preserves white space instead of collapsing it.
- `preserve-breaks` collapses spaces and tabs but preserves segment breaks as forced line breaks.
- `preserve-spaces` preserves space sequences while converting tabs and segment breaks to spaces.
- `break-spaces` preserves white space while also changing line-breaking behavior around preserved spaces.

The property is useful when whitespace behavior is part of the content rather than merely an authoring artifact. For example, an application can display user-entered plain text with intentional line breaks while still normalizing accidental runs of spaces. It can also help with code-like output, poetry, chat messages, imported text, or generated content where inserting `<br>` elements or wrapping everything in `<pre>` would be inconvenient or semantically inappropriate.

It also gives developers a more focused control than relying only on the broader `white-space` shorthand. You can express how whitespace should collapse separately from other text-wrapping decisions, making styles easier to understand and adjust.

There are important caveats. Because this property comes from a Level 4 draft, support may differ among browsers and among individual values. Do not assume that support for one value implies complete support for all of them. Test the exact behavior your interface needs, provide a suitable fallback where whitespace is essential, and remember that HTML parsing and CSS text processing can affect what counts as a segment break.

Further reading: [CSS Text Module Level 4 — `white-space-collapse`](https://drafts.csswg.org/css-text-4/#white-space-collapse-property)
