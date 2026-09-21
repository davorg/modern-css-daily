---
title: "prefers-color-scheme"
date: 2026-09-21
categories: ["CSS"]
tags: ["prefers-color-scheme"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#prefers-color-scheme"
---

`prefers-color-scheme` is a CSS media feature that lets a page respond to the user’s preference for a light or dark color theme. That preference may come from the operating system, browser, or another user-agent setting.

The feature is defined in CSS Media Queries Level 5. The linked CSSWG specification is an Editor’s Draft, so it is part of an evolving standards document rather than a finalized W3C Recommendation. No particular introduction date should be inferred from that status.

A minimal implementation starts with a default theme, then overrides it when the user prefers a dark appearance:

```css
body {
  color: #222;
  background-color: #fff;
}

@media (prefers-color-scheme: dark) {
  body {
    color: #eee;
    background-color: #121212;
  }
}
```

The current syntax defines two values:

- `light`: the user prefers a light appearance, or has not expressed an active preference.
- `dark`: the user prefers a dark appearance.

The media feature only reports a preference; it does not create a complete theme automatically. Developers still need to choose suitable colors for text, backgrounds, borders, controls, images, focus indicators, and interaction states.

This is useful today because it lets sites respect a preference users may already have set elsewhere. A dark theme can be applied without requiring every visitor to find and change a site-specific setting. It also works as progressive enhancement: browsers that do not match the dark query continue using the base light styles.

Treat the preference as a helpful default, not an absolute instruction. Some users may want a different theme for a particular site, so applications can still provide a manual theme control. If they do, they should decide clearly whether that explicit choice overrides the media query and how the choice is stored.

There are other caveats. Do not assume that every device or browser exposes the same underlying setting. Avoid relying on the media query as the only way to make content usable. Both themes still need adequate contrast, visible focus styles, and testing across all component states. Also ensure the unconditionally declared base styles form a complete, readable fallback.

Finally, because the specification is still an Editor’s Draft, check current documentation and test the browsers relevant to your project rather than relying on guessed version numbers or support percentages.

Further reading: [CSS Media Queries Level 5 — `prefers-color-scheme`](https://drafts.csswg.org/mediaqueries-5/#prefers-color-scheme)
