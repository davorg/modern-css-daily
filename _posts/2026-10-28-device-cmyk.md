---
title: "device-cmyk()"
date: 2026-10-28
categories: ["CSS"]
tags: ["device-cmyk()"]
layout: single
source: "https://drafts.csswg.org/css-color-5/#device-cmyk"
---

`device-cmyk()` lets CSS express a color as device-dependent cyan, magenta, yellow, and black components. It is aimed primarily at printing and other CMYK-oriented output, where authors may need to request specific channel values rather than rely on a renderer to convert an RGB color.

The feature is defined in the in-progress CSS Color Module Level 5 draft. It is not yet a finished W3C Recommendation, so its availability and behavior should be verified in every browser, print renderer, or HTML-to-PDF tool you plan to use.

A practical declaration can provide both ordinary CSS fallback and the function’s optional fallback color:

```css
.brand-mark {
  color: rgb(220 0 0);
  color: device-cmyk(0% 100% 100% 0%, rgb(220 0 0));
}
```

The four percentages represent cyan, magenta, yellow, and black, in that order. In this example, an implementation that does not recognize `device-cmyk()` will discard the second declaration and retain the preceding `rgb()` value. The fallback inside `device-cmyk()` is available to implementations that recognize the function but cannot use the requested CMYK color.

This is useful when CSS is part of a controlled print workflow—for example, generating brochures, labels, or print-ready PDFs with a renderer known to implement the feature. It allows designers and print providers to communicate familiar CMYK channel values directly, avoiding an unspecified RGB-to-CMYK choice at authoring time.

The important caveat is that “device” is literal: these values are device-dependent. The same CMYK percentages can produce visibly different results on different printers, inks, papers, or rendering pipelines. `device-cmyk()` does not attach an ICC profile or turn CMYK values into a portable, device-independent color specification. It is best treated as an escape hatch for a known output environment, not as a general replacement for modern CSS color spaces.

Support is also not sufficiently universal to assume that ordinary web browsers or print tools will honor the function. Test actual output, retain a conventional fallback declaration, and confirm requirements with the print service or PDF processor being used. Even when supported, final production output may still be affected by color management, raster image processors, and printer settings outside CSS.

Further reading: [CSS Color Module Level 5: Device-dependent CMYK Colors](https://drafts.csswg.org/css-color-5/#device-cmyk)
