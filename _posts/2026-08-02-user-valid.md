---
title: ":user-valid"
date: 2026-08-02
categories: ["CSS"]
tags: [":user-valid"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#user-pseudos"
---

`:user-valid` is a CSS pseudo-class for styling form controls whose values satisfy their validation constraints—but only after the user has significantly interacted with them. This differs from `:valid`, which may match a control immediately, even before the user has touched the form.

The pseudo-class is defined in the Selectors Level 4 specification. That specification remains a draft, so details and implementations may continue to evolve; it should not be treated as a fully finalized web standard.

A minimal example:

```html
<form>
  <label for="email">Email</label>
  <input id="email" name="email" type="email" required>
  <button>Subscribe</button>
</form>
```

```css
input:user-valid {
  border: 2px solid green;
}
```

Here, the input can match `:user-valid` when its value is a valid email address, satisfies the `required` constraint, and the browser considers the user to have significantly interacted with it.

This is useful because validation styling can otherwise appear too early. For example, an empty optional field may match `:valid` as soon as the page loads. Giving that untouched field a green border or check mark can be distracting or misleading. `:user-valid` lets positive feedback appear at a more relevant point in the interaction.

There is also a corresponding `:user-invalid` pseudo-class for invalid input:

```css
input:user-invalid {
  border: 2px solid crimson;
}
```

Together, these selectors can provide validation feedback without JavaScript while avoiding some of the premature styling associated with `:valid` and `:invalid`.

There are important caveats. The browser determines when interaction is significant enough for these pseudo-classes to apply, so do not assume a specific event such as `input`, `change`, or `blur` is always the trigger. They reflect the platform’s validation state; they do not add custom validation rules, display error messages, or replace accessible instructions. Color alone should not communicate success or failure.

Browser support is not uniform, and behavior should be tested in the browsers your project targets. Use `:user-valid` as a progressive enhancement, and retain an understandable form experience when the selector is unavailable. For critical custom validation workflows, JavaScript-managed classes may still be appropriate.

Further reading: [Selectors Level 4: User-interaction pseudo-classes](https://drafts.csswg.org/selectors-4/#user-pseudos)
