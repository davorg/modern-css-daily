---
title: "scripting"
date: 2026-09-13
categories: ["CSS"]
tags: ["scripting"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-5/#scripting"
---

The `scripting` CSS media feature lets a stylesheet adapt to whether scripting is available and active for the current document. It is defined in Media Queries Level 5, which remains an evolving draft rather than a finalized, universally implemented standard.

The feature has three discrete values:

- `none`: scripting is unsupported or currently turned off.
- `initial-only`: scripting is enabled during the initial page load but not afterward.
- `enabled`: scripting is supported and active for the document.

A progressive-enhancement pattern can keep a non-scripted interface as the default, then expose interactive controls when scripting is enabled:

```css
.static-navigation {
  display: block;
}

.interactive-navigation {
  display: none;
}

@media (scripting: enabled) {
  .static-navigation {
    display: none;
  }

  .interactive-navigation {
    display: block;
  }
}
```

This is useful because it expresses a scripting-dependent presentation choice directly in CSS. Without it, sites often add a class such as `js` to the root element from JavaScript, or rely on HTML’s `<noscript>` element. The media feature can reduce that coordination for cases where CSS only needs to choose between scripted and non-scripted presentations.

The `initial-only` value also accounts for environments that can run scripts while initially constructing a document but cannot continue running them afterward. Authors can target that state explicitly when it matters:

```css
@media (scripting: initial-only) {
  .requires-live-scripting {
    display: none;
  }
}
```

There are important caveats. Browser support should be checked before relying on this feature; do not assume every browser or embedded web view recognizes it. An unsupported media feature will not provide the intended branching, so the base styles should remain a usable fallback.

Also, `(scripting: enabled)` reports that scripting is supported and active—not that your particular JavaScript file downloaded, executed successfully, initialized a component, or remained error-free. It should not replace application-level state such as an `is-ready` class added after successful initialization. Use `scripting` for broad progressive enhancement, while using explicit DOM state for component readiness.

Finally, test the relevant states where possible. A page should remain understandable and navigable when scripting is unavailable, when the query itself is unsupported, and when JavaScript fails independently.

Further reading: [CSS Media Queries Level 5: `scripting`](https://drafts.csswg.org/mediaqueries-5/#scripting)
