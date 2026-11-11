---
title: "print-color-adjust"
date: 2026-11-11
categories: ["CSS"]
tags: ["print-color-adjust"]
layout: single
source: "https://drafts.csswg.org/css-color-adjust-1/#propdef-print-color-adjust"
---

`print-color-adjust` lets authors tell the user agent whether it may alter an element’s colors when producing printed or similar output. Browsers often make such adjustments to save ink, improve contrast, or accommodate printer limitations—for example, by omitting background colors.

The property is defined in CSS Color Adjustment Module Level 1, which remains a draft rather than a finalized W3C Recommendation. Its current syntax has two values:

- `economy` — the initial value. The user agent may adjust colors and styles as it considers appropriate for the output device.
- `exact` — indicates that the chosen colors are important and should not be changed unless the user has requested adjustments.

A minimal example:

```css
@media print {
  .invoice-summary {
    print-color-adjust: exact;
  }
}
```

This asks the browser to preserve the colors used in `.invoice-summary` when printing. Because `print-color-adjust` is inherited, the hint also applies to its descendants unless they override it.

The property is useful when color is more than decoration. A chart may rely on distinct fills to communicate categories. Alternating table-row backgrounds may be necessary for readability. A warning box, receipt, ticket, or form might use a background to distinguish critical information. Applying `exact` to those specific areas tells the browser that its usual ink-saving adjustments could damage the document’s meaning.

Prefer targeted use rather than applying `exact` to the entire page. Most printed content benefits from the default `economy` behavior, especially when large decorative backgrounds would consume substantial ink or toner.

There are important caveats. `exact` is a hint about user-agent adjustments, not a guarantee that printed output will perfectly match the screen. Users can explicitly choose print settings that override the author’s preference, and printer hardware, color management, paper, and PDF workflows can all affect the result. Browser support and print behavior may also differ, so test the unprefixed property in the browsers and output paths your application supports. Documents should remain understandable if backgrounds or other color details are not preserved.

Further reading: [CSS Color Adjustment Module Level 1 — `print-color-adjust`](https://drafts.csswg.org/css-color-adjust-1/#propdef-print-color-adjust)
