---
title: "background-blend-mode"
date: 2026-10-02
categories: ["CSS"]
tags: ["background-blend-mode"]
layout: single
source: "https://drafts.csswg.org/compositing-2/#propdef-background-blend-mode"
---

`background-blend-mode` controls how an element’s background images blend with one another and with its background color. It uses blend modes familiar from image-editing software, such as `multiply`, `screen`, and `overlay`, but applies them during browser rendering.

The property is defined by the CSS Compositing and Blending Level 2 specification. The cited document is an Editor’s Draft, not a final W3C Recommendation, so details may still be revised. There is no need to associate the feature with a precise introduction date.

A minimal example combines a background image with a solid color:

```css
.card {
  background-color: rebeccapurple;
  background-image: url("texture.jpg");
  background-blend-mode: multiply;
}
```

Here, `multiply` blends the image with the purple background. The result depends on the colors and transparency in the source image.

The property accepts a comma-separated list of blend modes. Each value corresponds to a background image in the same order as the `background-image` list, starting with the topmost layer. If there are fewer blend modes than background images, the list is repeated; extra values are ignored.

```css
.banner {
  background-color: navy;
  background-image:
    linear-gradient(to right, gold, transparent),
    url("landscape.jpg");
  background-blend-mode: screen, multiply;
}
```

This is useful for tinting photographs, combining textures and gradients, adapting reusable artwork to different themes, or producing decorative effects without generating a separate image for every color variation. Because the browser performs the blending, responsive backgrounds and CSS-driven theme changes remain straightforward.

There are important limits. `background-blend-mode` affects an element’s background layers, not its foreground content. Those backgrounds are blended as an isolated group, so they do not blend directly with content behind the element. For blending an entire element with its backdrop, `mix-blend-mode` is a different feature.

Blend results can vary dramatically with the source artwork, and they may reduce text contrast or obscure important details. Check accessibility in every relevant state. Treat the effect as an enhancement where practical: if the declaration is unsupported or invalid, the background images and color can still render without the requested blending. Consult current compatibility data and test in the browsers required by your project rather than relying on assumed versions or percentages.

Further reading: [CSS Compositing and Blending Level 2 — `background-blend-mode`](https://drafts.csswg.org/compositing-2/#propdef-background-blend-mode)
