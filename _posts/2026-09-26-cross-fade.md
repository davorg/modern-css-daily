---
title: "cross-fade()"
date: 2026-09-26
categories: ["CSS"]
tags: ["cross-fade()"]
layout: single
source: "https://drafts.csswg.org/css-images-4/#cross-fade-function"
---

`cross-fade()` creates a CSS image by blending two or more images, colors, or other CSS-generated images. Each input can have a percentage indicating its contribution to the result. This makes it possible to express a blend directly in CSS instead of preparing intermediate image files.

The function is defined in the evolving **CSS Images Module Level 4** draft. It should therefore be treated as an emerging feature rather than something that is consistently available across browsers. In particular, some implementations may support only nonstandard forms rather than the current specification syntax.

A minimal example with a fallback looks like this:

```css
.banner {
  background-image: url("/images/day.jpg");
  background-image: cross-fade(
    url("/images/day.jpg") 40%,
    url("/images/night.jpg") 60%
  );
}
```

The second declaration uses the current syntax: a comma-separated list of images or colors, each optionally paired with a percentage. Here, the result contains a 40% contribution from the daytime image and a 60% contribution from the nighttime image.

The first declaration is important. Browsers that do not recognize the standards-based `cross-fade()` value will discard that declaration and retain the ordinary background image. This makes the feature suitable for progressive enhancement when a static fallback is acceptable.

`cross-fade()` is useful when an interface needs a blended visual state—for example, combining light and dark artwork, producing an intermediate state between two illustrations, or mixing a gradient with an image. Keeping the blend in CSS can reduce the need to export multiple precomposed assets. Because the result is an `<image>`, it can be used anywhere the accepting property allows CSS images, not only with `background-image`.

There are important caveats. Support for the specification’s current syntax is not uniform, so test in every browser relevant to your project. Do not assume that recognition of a similarly named, nonstandard function means the standards-based form will work. Also remember that `cross-fade()` only defines the resulting image; it does not by itself create interaction state, timing, or a transition trigger.

Finally, background images are not a substitute for meaningful content. If an image conveys information, provide it through appropriate HTML and accessible text rather than relying solely on a CSS blend.

Further reading: [CSS Images Module Level 4 — `cross-fade()`](https://drafts.csswg.org/css-images-4/#cross-fade-function)
