---
title: "prefers-reduced-data"
date: 2026-11-02
categories: ["CSS"]
tags: ["prefers-reduced-data"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#prefers-reduced-data"
---

`prefers-reduced-data` is a CSS media feature that lets a page respond when a user has expressed a preference for using less network data. It is defined in the CSS Working Group’s draft of Media Queries Level 5, so it should be treated as an evolving feature rather than a finalized, universally available standard.

The feature has two values:

- `reduce`: the user prefers reduced data usage.
- `no-preference`: the user has not expressed that preference.

A data-conscious design can provide a lightweight baseline and load heavier decorative resources only when `no-preference` is reported:

```css
.promo {
  background-color: #243447;
}

@media (prefers-reduced-data: no-preference) {
  .promo {
    background-image: url("/images/promo.avif");
  }
}
```

This approach is deliberately progressive. Browsers that do not understand the media feature will ignore the media query, leaving the lightweight baseline in place. Alternatively, a site can use `(prefers-reduced-data: reduce)` to override an existing design, but unsupported browsers will then continue using the heavier default.

The feature is useful because large images, video, custom fonts, and other optional resources can be expensive for people using metered or constrained connections. Respecting a reduced-data preference can lower transfer costs and make a site feel faster. It also gives developers a declarative signal that can complement—not replace—general performance work.

Good uses include omitting decorative background images, avoiding automatic media playback, choosing simpler visual treatments, or reducing optional font downloads. Essential content and functionality should remain available. A reduced-data preference should not become a reason to hide information or deliver an incomplete experience.

There are important caveats. Do not assume that every browser or operating system exposes this preference, and check current compatibility information for your target audience rather than relying on old version tables. The media feature expresses a user preference; it is not a measurement of connection speed, bandwidth, or a site-specific data budget. CSS also cannot prevent resources that have already been requested elsewhere in the document from downloading. Resource selection therefore needs careful architecture, and JavaScript or suitable HTML mechanisms may still be necessary for some cases.

Use `prefers-reduced-data` as an optional enhancement, keep the default experience efficient, and test what actually transfers over the network.

Further reading: [Media Queries Level 5 — `prefers-reduced-data`](https://drafts.csswg.org/mediaqueries-5/#prefers-reduced-data)
