---
title: "::file-selector-button"
date: 2026-11-06
categories: ["CSS"]
tags: ["::file-selector-button"]
layout: single
source: "https://drafts.csswg.org/css-pseudo-4/#file-selector-button-pseudo"
---

File inputs are useful but have historically been awkward to style. The `::file-selector-button` pseudo-element provides a standard CSS hook for the button inside an `<input type="file">` control—the part users activate to open the file picker.

It is defined by the CSS Pseudo-Elements Module Level 4 specification. That module is still a draft rather than a finished W3C Recommendation, so details may evolve. The specification describes `::file-selector-button` as an element-backed pseudo-element targeting the file selector button when the user agent renders one.

A minimal example looks like this:

```html
<label for="avatar">Choose an avatar:</label>
<input id="avatar" name="avatar" type="file">
```

```css
input[type="file"]::file-selector-button {
  padding: 0.5rem 0.75rem;
  color: white;
  background: rebeccapurple;
  border: 0;
  border-radius: 0.25rem;
  cursor: pointer;
}
```

The selector applies styles to the button, not to the entire file input. You can style the surrounding `<input>` separately:

```css
input[type="file"] {
  font: inherit;
  color: #333;
}
```

This is useful because it lets developers bring file-upload controls closer to a site’s visual design without replacing the native input with custom JavaScript. The browser still handles opening the platform’s file picker and managing the selected file. Keeping the real file input also avoids many of the semantic, keyboard, and form-integration problems that can arise with fully custom controls.

There are some important caveats. The pseudo-element targets only the selector button; it does not independently target the filename or other text displayed by the control. The specification also accounts for user agents that may not render such a button, so applications should not depend on its exact appearance or internal layout.

Because this feature belongs to a draft specification and native form controls can vary across browsers and operating systems, test the result in the environments your project supports. Keep the underlying input usable without these styles. If a browser does not recognize the pseudo-element, the standalone CSS rule will not style the button, but the file input should retain its default presentation and functionality.

Further reading: [CSS Pseudo-Elements Module Level 4 — `::file-selector-button`](https://drafts.csswg.org/css-pseudo-4/#file-selector-button-pseudo)
