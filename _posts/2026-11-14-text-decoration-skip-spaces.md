---
title: "text-decoration-skip-spaces"
date: 2026-11-14
categories: ["CSS"]
tags: ["text-decoration-skip-spaces"]
layout: single
source: "https://drafts.csswg.org/css-text-decor-4/#text-decoration-skip-spaces-property"
---

`text-decoration-skip-spaces` controls whether a text decoration—such as an underline, overline, or line-through—skips spaces at the start or end of a line. It is useful when a decoration would otherwise extend through whitespace and create a visually awkward line beyond the text itself.

The property is defined in the CSS Text Decoration Module Level 4 specification. That specification is currently an Editor’s Draft, so the feature is not yet part of a finalized CSS Recommendation and may still change.

A minimal example looks like this:

```css
.decorated {
  text-decoration-line: underline;
  text-decoration-skip-spaces: start end;
}
```

The `start` value skips spaces at the start of each line, while `end` skips spaces at the end. Because the property’s syntax allows these keywords to be combined, `start end` applies both behaviors. The other defined value is `none`, which does not skip spaces.

This property is especially relevant for decorated inline content that wraps onto multiple lines. For example, a long underlined link may contain whitespace at a wrap boundary. Skipping that whitespace can make each visible segment of the underline align more closely with the actual text.

It also provides a declarative alternative to restructuring markup, inserting extra spans, or approximating the effect with backgrounds and pseudo-elements. Because `start` and `end` describe logical line positions rather than hard-coded left and right sides, the property also fits naturally into CSS layouts with different writing directions.

Do not confuse `text-decoration-skip-spaces` with `text-decoration-skip-ink`. The latter controls whether a decoration avoids parts of glyphs, such as letter descenders; `text-decoration-skip-spaces` is specifically concerned with spaces at line boundaries.

The main caveat is implementation support. Because this is a draft feature, browsers may not implement it consistently—or at all. Check the browsers relevant to your project and test the rendered result rather than assuming support. An unsupported declaration will normally be ignored, leaving the browser’s existing text-decoration behavior in place, so the property can often be used as progressive enhancement. If the visual distinction is important, consider guarding related styling with an `@supports` query:

```css
@supports (text-decoration-skip-spaces: start end) {
  .decorated {
    text-decoration-skip-spaces: start end;
  }
}
```

**Further reading:** [CSS Text Decoration Module Level 4: `text-decoration-skip-spaces`](https://drafts.csswg.org/css-text-decor-4/#text-decoration-skip-spaces-property)
