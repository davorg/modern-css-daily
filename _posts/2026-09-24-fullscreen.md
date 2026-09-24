---
title: ":fullscreen"
date: 2026-09-24
categories: ["CSS"]
tags: [":fullscreen"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#fullscreen-pseudo"
---

The `:fullscreen` CSS pseudo-class matches an element while it is being displayed in fullscreen mode. It lets a page respond to fullscreen state directly in CSS, without adding and removing a separate class from JavaScript.

`:fullscreen` is specified in the Selectors Level 4 draft, with fullscreen behavior defined by the Fullscreen standard. Because Selectors Level 4 remains a draft, details can continue to be refined; however, `:fullscreen` is available for practical use in modern web development. The current, unprefixed syntax is simply `:fullscreen`.

```html
<div class="viewer">
  <video src="movie.mp4" controls></video>
</div>

<style>
  .viewer:fullscreen {
    display: grid;
    place-items: center;
    background: black;
  }

  .viewer:fullscreen video {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
</style>
```

If the `.viewer` element enters fullscreen mode—for example, after a script calls `viewer.requestFullscreen()` in response to a user action—the first rule matches it. The second rule then styles its descendant video in that context.

This is useful because fullscreen layouts often need different choices from ordinary page layouts. A media viewer might switch to a black background, center its content, enlarge controls, remove decorative borders, or make an image or video fill the available space. Using `:fullscreen` keeps those presentation changes in CSS and ties them to the browser’s actual fullscreen state. There is no need to keep a custom `is-fullscreen` class synchronized with the Fullscreen API.

The pseudo-class does not itself make an element fullscreen. Entering fullscreen is handled separately, usually through the Fullscreen API, and is subject to browser security rules. A request may require transient user activation, and fullscreen can be restricted in embedded documents or by applicable permissions policy. Users and browsers can also exit fullscreen independently, at which point the selector stops matching.

Fullscreen rendering may involve user-agent behavior and default styles in addition to your own rules, so test the complete experience rather than assuming fullscreen is only a larger viewport. Also verify behavior in the browsers and embedding environments your project supports. Avoid relying on historical prefixed selectors in new code unless maintaining a specifically tested legacy codebase.

Further reading: [Selectors Level 4 — The Fullscreen Pseudo-class](https://drafts.csswg.org/selectors-4/#fullscreen-pseudo)
