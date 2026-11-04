---
title: "::highlight()"
date: 2026-11-04
categories: ["CSS"]
tags: ["::highlight()"]
layout: single
source: "https://drafts.csswg.org/css-highlight-api-1/#custom-highlight-pseudo"
---

`::highlight()` styles arbitrary text ranges without wrapping them in extra DOM elements. JavaScript creates one or more ranges, adds them to a `Highlight`, and registers that highlight under a name. CSS then targets the registered name with the `::highlight(<custom-ident>)` pseudo-element.

The feature is defined in the **CSS Custom Highlight API Module Level 1**, which is an Editor’s Draft and therefore remains a work in progress. It should be treated as a progressive enhancement rather than assumed to be available everywhere.

Here is a minimal example that highlights one word:

```html
<p id="text">CSS highlights text.</p>

<style>
  ::highlight(search-result) {
    background-color: gold;
    color: black;
  }
</style>

<script>
  const textNode = document.querySelector("#text").firstChild;

  const range = new Range();
  range.setStart(textNode, 4);
  range.setEnd(textNode, 14);

  const highlight = new Highlight(range);
  CSS.highlights.set("search-result", highlight);
</script>
```

The name passed to `CSS.highlights.set()` must match the custom identifier in `::highlight()`. A single `Highlight` can contain multiple ranges, making it convenient to style every match for a search term with one CSS rule.

This is useful for interfaces that need temporary, selection-like visual annotations: search results, spelling or grammar warnings, code diagnostics, comments, or document review tools. Previously, developers often wrapped matching text in `<span>` elements. That approach mutates the document structure, can complicate text processing, and may interfere with application code. Custom highlights keep those visual ranges separate from the content’s DOM structure.

There are important caveats. Browser support is not universal, so check for both the JavaScript API and registry before using them:

```js
if ("Highlight" in globalThis && globalThis.CSS?.highlights) {
  // Custom highlights are available.
}
```

Highlight pseudo-elements also support only the properties allowed for highlights. They are not ordinary generated boxes, so declarations intended to affect layout—such as padding or borders—should not be expected to work. Overlapping highlights and inherited styles can also require careful testing.

Finally, custom highlights are primarily visual. Because they do not add semantic DOM elements, they are not a substitute for meaningful markup, accessible controls, or content that assistive technology must interpret structurally.

Further reading: [CSS Custom Highlight API Module Level 1 — Custom Highlight Pseudo-element](https://drafts.csswg.org/css-highlight-api-1/#custom-highlight-pseudo)
