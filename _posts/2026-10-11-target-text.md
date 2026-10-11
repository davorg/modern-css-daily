---
title: "::target-text"
date: 2026-10-11
categories: ["CSS"]
tags: ["::target-text"]
layout: single
source: "https://drafts.csswg.org/css-pseudo-4/#selectordef-target-text"
---

`::target-text` is a CSS pseudo-element for styling text identified by a URL’s text fragment directive. When a browser follows such a link, it can scroll directly to a particular passage rather than merely to an element with an `id`. `::target-text` lets the page author control how that targeted passage is highlighted.

The feature is defined in the CSS Pseudo-Elements Module Level 4 specification. That module remains draft standards work, so developers should not assume complete or identical implementation across browsers.

The current syntax is straightforward:

```css
::target-text {
  color: black;
  background-color: gold;
}
```

This rule changes the foreground and background colors of the targeted text. The pseudo-element does not create a text fragment, choose which text a URL targets, or affect ordinary element fragment links. It only styles text that the browser has already identified as the target of a text fragment.

This is useful because links to exact passages are increasingly practical in documentation, articles, issue reports, and review workflows. A person can share a link that draws attention to a sentence or phrase, while the site can make that destination fit its own color palette. Custom styling can also improve contrast when the browser’s default highlight does not work well with a page’s design.

Keep the styling simple and readable. As a highlight pseudo-element, `::target-text` is subject to the specification’s highlight styling model rather than behaving like a normal generated box. The example above uses `color` and `background-color`, which are appropriate highlight properties.

There are several caveats:

- Browser support is not universal, so test the browsers relevant to your audience.
- A browser may support text-fragment navigation without supporting author styling through `::target-text`.
- The rule has no effect when a page is opened normally or through a conventional `#element-id` fragment.
- CSS cannot use `::target-text` to discover the targeted words, modify the document structure, or generate a shareable URL.
- Choose colors with sufficient contrast, and do not rely on the custom highlight as the only way to communicate important information.

Used as progressive enhancement, `::target-text` provides a small but valuable way to integrate passage-level links into a site’s visual design. Unsupported browsers can still display the document, and supporting browsers can apply the customized highlight.

Further reading: [CSS Pseudo-Elements Module Level 4 — `::target-text`](https://drafts.csswg.org/css-pseudo-4/#selectordef-target-text)
