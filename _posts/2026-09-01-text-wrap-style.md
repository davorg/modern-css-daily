---
title: "text-wrap-style"
date: 2026-09-01
categories: ["CSS"]
tags: ["text-wrap-style"]
layout: single
source: "https://drafts.csswg.org/css-text-4/#text-wrap-style-property"
---

`text-wrap-style` lets authors influence how a browser chooses line breaks when text wraps. Unlike properties that enable or disable wrapping, it selects a wrapping strategy: the browser can prioritize speed, balanced line lengths, typographic quality, or stability during editing.

The property is defined in **CSS Text Module Level 4**, which remains a draft rather than a finalized W3C Recommendation. Implementations may therefore vary, both in which values they recognize and in how their line-breaking algorithms interpret them.

A minimal example balances the lines of a heading:

```css
.card-title {
  text-wrap-style: balance;
}
```

`balance` asks the browser to make the lines more even in length. It is particularly useful for headings, captions, callouts, and other short blocks where an awkwardly short final line can make a component look unfinished. The specification allows user agents to limit how many lines they attempt to balance, so it should not be treated as a general-purpose layout mechanism for long articles.

Other values defined by the specification include `auto`, which leaves the strategy to the browser; `pretty`, which asks the browser to favor higher-quality typography over wrapping speed; and `stable`, which prevents lines before the line currently being edited from being rewrapped in editable content. Outside that editing case, `stable` behaves like `auto`.

The feature is useful today as progressive enhancement. A balanced heading or more carefully wrapped paragraph can improve readability without changing the document structure, adding manual `<br>` elements, or inserting non-breaking spaces that become problematic at different viewport sizes. Because `text-wrap-style` is inherited, it can also be applied at an appropriate container level when several descendants should share the same strategy.

There are important caveats. Line-breaking quality is deliberately user-agent-defined, so two browsers need not produce identical lines. Support may differ by browser and by value; consult current compatibility data for your target audience rather than assuming uniform availability. Unsupported declarations are ignored, leaving normal wrapping as the fallback. Also remember that the property cannot make an unsuitable width responsive, guarantee a specific number of lines, or replace proper overflow and white-space handling.

Use it where improved wrapping is beneficial, but let the layout remain correct without it.

**Further reading:** [CSS Text Module Level 4 — `text-wrap-style`](https://drafts.csswg.org/css-text-4/#text-wrap-style-property)
