---
title: ":popover-open"
date: 2026-08-18
categories: ["CSS"]
tags: [":popover-open"]
layout: single
source: "https://drafts.csswg.org/selectors-4/"
---

`:popover-open` is a CSS pseudo-class that matches an element while it is in the **popover showing state**. It lets CSS respond to a popover’s actual open state without adding or removing a class in JavaScript.

The pseudo-class is defined in **Selectors Level 4**, which is published as an Editor’s Draft. It should therefore be treated as an evolving standard rather than a finalized W3C Recommendation. The specification does not require authors to track when the feature was introduced.

A minimal example combines `:popover-open` with HTML’s Popover API:

```html
<button popovertarget="help">Show help</button>

<div id="help" popover>
  Use a strong, unique password.
</div>

<style>
  #help {
    padding: 1rem;
    border: 2px solid gray;
  }

  #help:popover-open {
    border-color: rebeccapurple;
    background: lavender;
  }
</style>
```

The `popover` attribute makes the `<div>` a popover, while `popovertarget="help"` connects the button to it. When the popover is showing, `#help:popover-open` matches and applies the highlighted styles. When it is hidden, that rule no longer matches.

This is more precise than an attribute selector such as `[popover]`. The attribute selector matches every element carrying the `popover` attribute, regardless of whether it is currently visible. `:popover-open` represents the live state.

That distinction is useful for menus, help panels, disclosures, and other temporary interfaces. Developers can style an open popover declaratively—for example, changing its border, background, shadow, or internal layout—without maintaining a parallel `.open` class. It also works regardless of whether the popover was shown through a declarative trigger or script, because the selector follows the platform-managed state.

There are caveats. The selector depends on support for both popovers and the `:popover-open` pseudo-class, so check compatibility for the browsers required by your project rather than assuming universal availability. Keep essential content and controls usable when the state-specific rule is ignored. If unsupported selectors need to coexist with fallback selectors, placing them in separate rules can prevent an unsupported selector from invalidating an entire selector list.

Finally, `:popover-open` is a styling hook, not an event mechanism or a replacement for application logic. Use the relevant HTML and JavaScript APIs when code must react to popover behavior.

Further reading: [CSS Selectors Level 4](https://drafts.csswg.org/selectors-4/)
