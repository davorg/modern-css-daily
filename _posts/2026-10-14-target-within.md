---
title: ":target-within"
date: 2026-10-14
categories: ["CSS"]
tags: [":target-within"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#the-target-within-pseudo"
---

`:target-within` is a relational pseudo-class for styling a URL target and its containing elements. An element matches when it is itself the target of the document URL’s fragment identifier, or when one of its descendants is the target.

For example, visiting or following a link to `#installation` makes the `<h2>` the target. Its containing `<section>` then matches `:target-within`:

```html
<nav>
  <a href="#installation">Installation</a>
</nav>

<section>
  <h2 id="installation">Installation</h2>
  <p>Run the package installer.</p>
</section>

<style>
  section:target-within {
    border-left: 4px solid royalblue;
    background: aliceblue;
  }
</style>
```

The syntax is simply `:target-within`. In this example, it allows the whole section to be highlighted even though the fragment identifier points to a heading inside it. If the `<section>` itself were the target, it would also match.

This is useful for documentation, FAQs, long articles, settings pages, and other interfaces that use fragment links. The existing `:target` pseudo-class can style the exact target, but authors often want to emphasize a larger region around it. Without `:target-within`, that can require changing the markup, applying the target’s `id` to a container, or using JavaScript to locate and style an ancestor.

`:target-within` is defined in Selectors Level 4. The linked specification is a draft rather than a finalized W3C Recommendation, so the feature’s details and implementation status should not be treated as universally settled.

Browser support is therefore an important caveat. Check current compatibility information and test in the browsers required by your project before relying on it. Use it as a progressive enhancement when possible: keep the content readable and navigable without the ancestor highlight, and consider a separate `:target` rule as a fallback for the directly targeted element.

If you write fallback selectors, keep them in separate rules. An implementation that does not recognize `:target-within` may reject a normal selector list containing it, which could also discard otherwise supported selectors in that same rule.

**Further reading:** [Selectors Level 4 — `:target-within`](https://drafts.csswg.org/selectors-4/#the-target-within-pseudo)
