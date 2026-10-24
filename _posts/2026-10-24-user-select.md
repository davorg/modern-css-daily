---
title: "user-select"
date: 2026-10-24
categories: ["CSS"]
tags: ["user-select"]
layout: single
source: "https://drafts.csswg.org/css-ui-4/#propdef-user-select"
---

`user-select` controls whether and how users can select an element’s content. It is defined in CSS Basic User Interface Module Level 4, an evolving CSS Working Group Editor’s Draft rather than a finished Recommendation. The feature has existed in implementations for some time, but its behavior and support are not identical everywhere.

A common use is preventing accidental text selection on an interactive surface:

```css
.drag-handle {
  user-select: none;
}
```

This is useful for drag handles, custom controls, maps, and similar interfaces where pointer movement should not leave text highlighted.

The specification defines five values:

- `auto` lets the browser determine the behavior. Although `user-select` is not inherited, `auto` can resolve according to the parent’s used value. It also has specific behavior for generated content and editable elements.
- `text` allows ordinary text selection without imposing an additional constraint.
- `none` prevents the element’s content from participating in normal user selection.
- `contain` constrains a selection that begins inside the element so it cannot extend outside it.
- `all` makes the element’s content atomic for selection: a selection that would include only part of it must include all of it.

`all` can be convenient for code snippets or other short content intended to be copied as a unit:

```css
.copyable-code {
  user-select: all;
}
```

Use the property selectively. Text selection is more than a prelude to copying: people may use highlighting to follow what they are reading, invoke browser or assistive features, quote content, or translate it. Applying `user-select: none` broadly can therefore make a page less usable.

It is also not a security or copy-protection feature. Content remains available to scripts, developer tools, accessibility APIs, and other means. Use it only to improve interaction behavior, not to protect sensitive information.

Finally, test the values you depend on in your supported browsers and input modes. Support and edge-case behavior are not uniform for every value, particularly `contain`, and interactions involving nested elements, editable content, or generated content may be less intuitive than a simple example suggests.

**Further reading:** [CSS Basic User Interface Module Level 4 — `user-select`](https://drafts.csswg.org/css-ui-4/#propdef-user-select)
