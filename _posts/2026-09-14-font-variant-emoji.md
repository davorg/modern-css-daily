---
title: "font-variant-emoji"
date: 2026-09-14
categories: ["CSS"]
tags: ["font-variant-emoji"]
layout: single
source: "https://drafts.csswg.org/css-fonts-4/#font-variant-emoji-prop"
---

`font-variant-emoji` controls whether emoji-capable characters are presented using text-style glyphs or emoji-style glyphs. It lets authors influence presentation through CSS instead of inserting Unicode variation selectors directly into content.

The property is defined in CSS Fonts Module Level 4. That module remains a draft, so the feature should be treated as an emerging standard: implementations may vary, and support should be tested in the browsers relevant to your project.

A minimal example:

```css
.code-label {
  font-variant-emoji: text;
}
```

```html
<span class="code-label">Status: ✅</span>
```

The specification defines four values:

- `normal` allows the user agent to choose the presentation.
- `text` requests text presentation.
- `emoji` requests emoji presentation.
- `unicode` follows the presentation specified by Unicode’s emoji properties.

This distinction matters because many Unicode characters can have either presentation. A symbol might appear as a monochrome glyph that follows the surrounding text, or as a colorful emoji with noticeably different sizing and visual weight.

Today, `font-variant-emoji` is useful when presentation is part of a component’s design rather than its content. Documentation, code samples, data tables, status labels, and compact controls may benefit from `text`, where a colorful emoji could be distracting. Conversely, messaging interfaces or expressive consumer-facing components may prefer `emoji`. Because the property inherits, it can also establish a presentation policy for an entire section:

```css
.documentation {
  font-variant-emoji: text;
}

.reactions {
  font-variant-emoji: emoji;
}
```

There are important caveats. Browser support is not uniform, so provide a design that remains understandable when the declaration is ignored. The property requests a presentation style; it does not guarantee a particular glyph, color palette, or artwork. Results still depend on the user agent, operating system, installed fonts, and available emoji glyphs.

Explicit Unicode variation selectors in the content can determine presentation independently of the surrounding CSS. The property also does not turn arbitrary characters into emoji; it applies only where Unicode defines relevant emoji presentation behavior.

Finally, treat this as visual styling, not semantics. Do not rely on the difference between text and emoji presentation to communicate information that is unavailable in the text or accessible name.

Further reading: [CSS Fonts Module Level 4 — `font-variant-emoji`](https://drafts.csswg.org/css-fonts-4/#font-variant-emoji-prop)
