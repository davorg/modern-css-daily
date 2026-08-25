---
title: ":user-invalid"
date: 2026-08-25
categories: ["CSS"]
tags: [":user-invalid"]
layout: single
source: "https://drafts.csswg.org/selectors-4/#user-pseudos"
---

`:user-invalid` is a CSS pseudo-class for styling a form control whose value is invalid after the user has significantly interacted with it. It uses the control’s existing validity state—such as an invalid email address or a missing required value—but avoids showing an error merely because an empty form has loaded.

That distinction makes it different from `:invalid`. A required, empty input can match `:invalid` immediately, which may cause a page to greet users with a collection of red fields before they have done anything. `:user-invalid` lets the browser delay that presentation until interaction makes the feedback relevant.

```html
<label for="email">Email address</label>
<input
  id="email"
  name="email"
  type="email"
  required
  aria-describedby="email-error"
>
<p id="email-error" class="error">Enter a valid email address.</p>

<style>
  .error {
    display: none;
    color: #b00020;
  }

  input:user-invalid {
    border: 2px solid #b00020;
  }

  input:user-invalid + .error {
    display: block;
  }
</style>
```

CSS does not perform the validation here. The `type="email"` and `required` attributes define the HTML validity constraints; `:user-invalid` selects the control when it is invalid and the user-interaction condition has been met.

The feature is specified in Selectors Level 4, which remains a draft specification. An important part of its design is that browsers determine when the user has “significantly interacted” with a control. That can include behavior around editing, changing focus, or attempting to submit a form. Do not rely on every browser exposing the invalid state at precisely the same moment.

`:user-invalid` is useful today as a progressive enhancement. Supporting browsers can provide less aggressive, better-timed validation feedback without JavaScript state classes. If a browser does not recognize the pseudo-class, these styling rules will not apply, while the form’s native HTML constraints can still operate. Check current compatibility information and test the interaction in your supported browsers rather than assuming uniform availability.

Finally, treat this as presentation rather than a complete validation experience. Provide understandable error text, do not communicate errors through color alone, and remember that revealing text with CSS does not guarantee it will be announced immediately by assistive technology. Server-side validation is still required.

Further reading: [Selectors Level 4: User-interaction pseudo-classes](https://drafts.csswg.org/selectors-4/#user-pseudos)
