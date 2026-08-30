---
title: "dynamic-range-limit"
date: 2026-08-30
categories: ["CSS"]
tags: ["dynamic-range-limit"]
layout: single
source: "https://drafts.csswg.org/css-color-hdr/#propdef-dynamic-range-limit"
---

HDR displays can render highlights far brighter than traditional standard dynamic range (SDR) content. CSS’s `dynamic-range-limit` property lets authors limit how much of that available brightness an element may use.

The property accepts three keyword values:

- `standard` limits content to the standard dynamic range.
- `constrained-high` permits high dynamic range while imposing a predefined constraint.
- `no-limit` imposes no author-requested limit, allowing the user agent to use the available dynamic range.

A minimal example:

```css
.hdr-preview {
  dynamic-range-limit: constrained-high;
}

.page-controls {
  dynamic-range-limit: standard;
}
```

This allows an HDR preview to retain brighter highlights while keeping surrounding controls within the standard range. The values describe dynamic-range limits rather than exact luminance in nits: actual output still depends on the display, operating environment, browser rendering, and the source content.

The property is useful because HDR is not always an all-or-nothing design choice. A photo, video, canvas, or visual effect might benefit from additional headroom, while nearby text and interface elements should remain visually stable. Limiting selected content can stop bright highlights from dominating the page’s hierarchy and can help authors create more deliberate transitions between SDR and HDR areas.

`dynamic-range-limit` does not turn SDR content into HDR, guarantee that HDR will be displayed, or increase a device’s physical capabilities. Likewise, `no-limit` means that CSS is not imposing this particular restriction; it does not promise maximum brightness.

The feature is defined in the CSS Color HDR Module Level 1 specification, which is an Editor’s Draft rather than a finalized W3C Recommendation. Its details may therefore change as the specification develops.

Implementation availability is another important caveat. Do not assume the property works in every browser, embedded web view, or display configuration. Test it in the environments relevant to your project and treat it as a progressive enhancement. Browsers that do not recognize the declaration will ignore it, leaving their existing HDR rendering behavior in place. Also test real HDR content on HDR hardware: an SDR screenshot or ordinary desktop monitor cannot fully demonstrate the result.

Further reading: [CSS Color HDR Module Level 1 — `dynamic-range-limit`](https://drafts.csswg.org/css-color-hdr/#propdef-dynamic-range-limit)
