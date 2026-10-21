---
title: "anchor-size()"
date: 2026-10-21
categories: ["CSS"]
tags: ["anchor-size()"]
layout: single
source: "https://drafts.csswg.org/css-anchor-position-1/#anchor-size-fn"
---

`anchor-size()` lets an anchor-positioned element use the dimensions of its anchor in a CSS value. A tooltip can match its trigger’s width, for example, without JavaScript measuring the trigger or observing resize events.

The function is defined by CSS Anchor Positioning Level 1. That specification is currently an Editor’s Draft, so the syntax and behavior remain subject to standards work rather than being a finalized web standard.

Here is a minimal example:

```html
<button class="trigger">Open menu</button>
<div class="panel">Menu content</div>
```

```css
.trigger {
  anchor-name: --trigger;
}

.panel {
  position: absolute;
  position-anchor: --trigger;

  top: anchor(bottom);
  left: anchor(left);
  inline-size: anchor-size(inline);
}
```

The button establishes a named anchor with `anchor-name`. The panel selects it as its default anchor using `position-anchor`. Its top and left insets are then positioned relative to the button, while `anchor-size(inline)` gives the panel the button’s inline size.

`anchor-size()` can also name the anchor directly and provide a fallback value:

```css
.panel {
  inline-size: anchor-size(--trigger inline, 12rem);
}
```

The function accepts physical dimensions such as `width` and `height`, logical dimensions such as `block` and `inline`, and `self-block` or `self-inline`, which interpret the requested axis in the positioned element’s writing mode. The optional fallback is used when the requested anchor size cannot otherwise be resolved. It does not make the declaration work in a browser that does not recognize `anchor-size()` at all.

This is useful today as a progressive enhancement. Common interface patterns—menus matching a button, callouts sized relative to a highlighted element, or overlays constrained by their trigger—can be expressed declaratively. CSS can respond automatically when content, fonts, layout, or writing mode changes, avoiding duplicated measurements in application code.

The main caveat is implementation availability: support is not universal, and developers should consult current compatibility data and test in their target browsers. Keep a conventional size declaration before the enhanced one so unsupported browsers retain usable styling:

```css
.panel {
  inline-size: 12rem;
  inline-size: anchor-size(--trigger inline, 12rem);
}
```

Anchor resolution also follows the specification’s rules for valid anchors and can fail when the named anchor is unavailable or unsuitable. Test unusual containing blocks, writing modes, and dynamic DOM changes.

**Further reading:** [CSS Anchor Positioning Level 1: `anchor-size()`](https://drafts.csswg.org/css-anchor-position-1/#anchor-size-fn)
