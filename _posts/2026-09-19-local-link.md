---
title: ":local-link"
date: 2026-09-19
categories: ["CSS"]
tags: [":local-link"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#local-link-pseudo"
---

`:local-link` is a CSS pseudo-class for identifying links that point to the document currently being viewed. It matches a hyperlink when its target’s absolute URL is the same as the current document’s URL, with any URL fragment ignored.

That makes it useful for highlighting the current page in site navigation:

```css
nav a:local-link {
  font-weight: 700;
  text-decoration: underline;
}
```

Given a navigation link to `/about`, this rule can match when the visitor is already on `/about`. A link to `/about#team` can also match because fragment identifiers do not affect the comparison.

The pseudo-class is defined in Selectors Level 4, which remains a draft CSS specification. Its current syntax is simply `:local-link`; it does not take an argument.

The main benefit is that CSS can recognize a current-page link without extra markup or application logic. Sites commonly add classes such as `active`, `selected`, or `current` on the server or with JavaScript. Where `:local-link` is available, the browser already has the URL information needed to express this state directly.

It can also improve the behavior of reusable navigation components. The same HTML can appear across many pages, while CSS automatically styles whichever link targets the current document. Beyond navigation, it can help distinguish self-referential links or links to sections within the current page.

There are important limits. `:local-link` does not match every internal or same-origin link; the target must resolve to the current document. Only the fragment is ignored, so URLs that differ in another component, such as the query string, should not be treated as equivalent current-document links.

Browser support is not sufficiently universal to assume that this selector will work for every visitor. Check current compatibility data for your target browsers, and do not make essential navigation behavior depend on it. In a browser that does not recognize the pseudo-class, the selector is invalid and the rule is ignored. Keep fallback styling in separate rules, or continue emitting an explicit current-page class when consistent presentation is required.

Because the feature is still specified in a draft, its definition may also change before the specification advances. It is best treated as a progressive enhancement rather than a replacement for established current-page indicators.

Further reading: [Selectors Level 4 — `:local-link`](https://drafts.csswg.org/selectors-4/#local-link-pseudo)
