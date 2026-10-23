---
title: ":picture-in-picture"
date: 2026-10-23
categories: ["CSS"]
tags: [":picture-in-picture"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#pip-state"
---

The `:picture-in-picture` CSS pseudo-class matches an element that is currently being displayed in picture-in-picture mode. It lets a page respond declaratively when, for example, a video has been moved into a floating picture-in-picture window.

The feature is defined in the Selectors Level 4 specification, which remains a draft. Consequently, implementation may vary between browsers, and developers should check current compatibility information before relying on it as an essential part of an interface.

A minimal example looks like this:

```html
<video controls src="movie.mp4"></video>
```

```css
video:picture-in-picture {
  outline: 4px solid rebeccapurple;
}
```

While the video is in picture-in-picture mode, it matches the selector and receives the outline. When it leaves that mode, it stops matching, so the style is removed automatically.

This is useful for communicating state in the original page. A site might mark the source video, adjust surrounding controls, or show a message explaining that playback is continuing in another window. Because the state is exposed as a pseudo-class, these visual changes can remain synchronized without JavaScript adding and removing a class.

For example, a nearby status message can be revealed with ordinary selectors:

```html
<video controls src="movie.mp4"></video>
<p class="pip-status">Playing in picture-in-picture mode</p>
```

```css
.pip-status {
  display: none;
}

video:picture-in-picture + .pip-status {
  display: block;
}
```

There are important limits. The selector does not request or activate picture-in-picture mode; it only matches an element that is already in that state. Entering picture-in-picture depends on the relevant browser API, user interaction requirements, browser policy, and platform capabilities.

The pseudo-class also targets the element in the document. It should not be treated as a mechanism for controlling the browser’s separate picture-in-picture window or its native interface. Finally, because this feature is specified in a draft and support is not uniform, provide a sensible default experience when the selector is unavailable.

**Further reading:** [Selectors Level 4: The Picture-in-Picture State Pseudo-class](https://drafts.csswg.org/selectors-4/#pip-state)
