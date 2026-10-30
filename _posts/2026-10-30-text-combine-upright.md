---
title: "text-combine-upright"
date: 2026-10-30
categories: ["CSS"]
tags: ["text-combine-upright"]
layout: single
source: "https://drafts.csswg.org/css-writing-modes-4/#text-combine-upright"
---

Vertical Japanese text sometimes sets a short sequence of characters—commonly two to four digits—horizontally within a single vertical line. This typographic convention is called *tate-chū-yoko*. CSS provides `text-combine-upright` for this purpose.

The property combines the text inside an inline element into one upright typographic unit when it appears in a vertical writing mode. The combined characters are laid out horizontally, while the surrounding text continues vertically.

```html
<p class="vertical">
  次の会議は<span class="combined">12</span>月です。
</p>
```

```css
.vertical {
  writing-mode: vertical-rl;
}

.combined {
  text-combine-upright: all;
}
```

Here, `12` is displayed as a horizontal unit within the vertical line. The current syntax defined by CSS Writing Modes Level 4 is:

```css
text-combine-upright: none | all;
```

`none` disables combination. `all` combines all text within the element, so authors should wrap only the characters intended to form one unit.

The feature is defined in the CSS Writing Modes Level 4 specification, which is a CSS Working Group draft rather than a finalized W3C Recommendation. It should therefore be treated as an evolving standard, even though implementations are available in browsers. Check current compatibility information and test in the browsers relevant to your project rather than relying on assumptions about versions or support percentages.

`text-combine-upright` is useful today for Japanese publishing, calendars, dates, counters, addresses, and other interfaces that use vertical typography. It avoids substituting images or manually positioning individual characters, while keeping the content as real text that can be copied, searched, translated, and styled.

There are several practical caveats. The property is intended for vertical writing modes and does not provide a general mechanism for rotating or compressing text in horizontal layouts. Because `all` combines the element’s entire text run, applying it to a long phrase can produce poor typography; keep combined spans short and explicit. Exact glyph sizing and compression can also depend on the font and user agent, so verify the result with the fonts and writing modes your site actually uses. As with any specialized typography, test selection, copy-and-paste behavior, and accessibility with your target browser and assistive-technology combinations.

**Further reading:** [CSS Writing Modes Level 4: `text-combine-upright`](https://drafts.csswg.org/css-writing-modes-4/#text-combine-upright)
