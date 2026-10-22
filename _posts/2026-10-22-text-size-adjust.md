---
title: "text-size-adjust"
date: 2026-10-22
categories: ["CSS"]
tags: ["text-size-adjust"]
layout: single
source: "https://drafts.csswg.org/css-size-adjust/#propdef-text-size-adjust"
---

`text-size-adjust` controls whether a user agent adjusts text sizes independently of the CSS `font-size`. This behavior—often called text inflation—can occur on small-screen devices when a page or text column is wider than the device’s display. The browser may enlarge text to improve readability without otherwise changing the page’s layout.

The property is defined in **CSS Mobile Text Size Adjustment Module Level 1**, currently an Editor’s Draft rather than a finalized Recommendation. Its standard syntax accepts `auto`, `none`, or a non-negative percentage:

- `auto` leaves the adjustment behavior to the user agent and is the initial value.
- `none` prevents text-size adjustment.
- A percentage specifies the adjustment factor. `100%` requests no increase or decrease.

A minimal example is:

```css
html {
  text-size-adjust: 100%;
}
```

The property applies to all elements and is inherited, so setting it on the root element establishes a document-wide value unless descendants override it.

This feature remains useful because mobile browsers may encounter pages whose layout suggests that the text would otherwise be too small. Automatic inflation can help with older, fixed-width pages, but it may produce unexpected typography in a carefully designed responsive interface. For example, headings and body text may no longer maintain the proportions intended by the design system. Setting an explicit percentage gives authors control over that adjustment.

Use it cautiously. Automatic text adjustment exists for readability, so disabling it is not a substitute for choosing accessible font sizes, sensible line lengths, and a responsive viewport. Test the result on narrow screens, at different orientations, and with user-controlled zoom or text settings. A page that depends on `text-size-adjust` to make small text acceptable likely needs broader typography or layout changes.

Implementation behavior and availability can vary across browsers and platforms. Do not assume the declaration will have an effect in every browser: unsupported declarations are ignored, and even supporting browsers may only apply adjustment in situations where their text-sizing algorithm is active. Because the specification is still a draft, consult current documentation and test the browsers relevant to your project.

**Further reading:** [CSS Mobile Text Size Adjustment Module Level 1](https://drafts.csswg.org/css-size-adjust/#propdef-text-size-adjust)
