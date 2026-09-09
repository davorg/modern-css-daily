---
title: "color-gamut"
date: 2026-09-09
categories: ["CSS"]
tags: ["color-gamut"]
layout: single
source: "https://drafts.csswg.org/mediaqueries-4/#color-gamut"
---

The `color-gamut` media feature lets CSS ask about the approximate range of colors supported by the user agent and the output device, such as the current display. It is defined in Media Queries Level 4. The linked specification is a CSS Working Group Editor’s Draft, so it should not be treated as a final W3C Recommendation.

The feature accepts three values:

- `srgb`: approximately the sRGB gamut or wider
- `p3`: approximately the Display P3 gamut or wider
- `rec2020`: approximately the Rec. 2020 gamut or wider

These values act as capability thresholds. A device matching `rec2020` also has a gamut at least as wide as `p3` and `srgb`. This makes progressive enhancement straightforward: provide a broadly suitable default, then opt into assets or styles intended for wider-gamut displays.

```css
.hero {
  background-image: url("hero-srgb.jpg");
}

@media (color-gamut: p3) {
  .hero {
    background-image: url("hero-p3.jpg");
  }
}
```

This example serves an sRGB image by default and substitutes a P3-oriented asset when the browser and output device report an approximately P3-or-wider gamut.

That is useful today because many sites need to work across displays with substantially different color capabilities. Photography, digital art, product imagery, data visualization, and brand colors can benefit from richer color on capable hardware without making wide-gamut output a requirement. The query can also help avoid sending a specialized asset when its additional color information would not be useful.

There are important caveats. `color-gamut` reports an approximate gamut, not a guarantee of color accuracy, calibration quality, brightness, contrast, or HDR capability. A match also does not prove that every part of your content pipeline is correctly color-managed. Images still need appropriate color profiles, and any CSS colors you use must employ syntax supported by the target browser.

The feature reflects the combination of the user agent and output device rather than the device in isolation. Results may therefore depend on the active display and browsing environment. If support for this media feature is uncertain in your target browsers, keep the default experience complete and treat wider-gamut rules strictly as an enhancement. Test on representative hardware rather than relying only on emulation.

Further reading: [CSS Media Queries Level 4 — `color-gamut`](https://drafts.csswg.org/mediaqueries-4/#color-gamut)
