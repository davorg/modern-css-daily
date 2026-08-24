---
title: "animation-composition"
date: 2026-08-24
categories: ["CSS"]
tags: ["animation-composition"]
layout: single
source: "https://drafts.csswg.org/css-animations-2/#animation-composition"
---

When multiple CSS animations affect the same property, their effects need a rule for combining values. `animation-composition` provides that rule. It is defined in CSS Animations Level 2, which is currently a draft specification rather than a finalized Recommendation.

The property accepts a comma-separated list of composition modes corresponding to the animations:

- `replace` — the animation’s value replaces the underlying value. This is the initial value.
- `add` — the animation’s value is added to the underlying value using the property’s addition operation.
- `accumulate` — the animation’s value is combined with the underlying value using the property’s accumulation operation.

“Add” does not necessarily mean ordinary numeric addition. The exact operation depends on the animated property. For transforms, for example, composition can combine transform operations.

Here is a minimal example in which translation and scaling are defined as independent animations but both contribute to `transform`:

```css
.card {
  animation:
    drift 2s ease-in-out infinite alternate,
    pulse 1s ease-in-out infinite alternate;
  animation-composition: add, add;
}

@keyframes drift {
  from { transform: translateX(0); }
  to   { transform: translateX(2rem); }
}

@keyframes pulse {
  from { transform: scale(1); }
  to   { transform: scale(1.08); }
}
```

Without additive composition, animations targeting the same property can replace one another according to the animation effect stack. With `add`, the translation and scale can both contribute to the resulting transform.

This is useful for keeping effects small and reusable. A movement animation, hover-like pulse, and application-state transition can be authored independently instead of being merged into one large set of keyframes. It can also help component code add an effect without having to reproduce every transform already applied elsewhere.

There are important caveats. Composition behavior depends on the property and its defined animation type; not every property or value has a useful additive or accumulative operation. The order in which effects are composed can also affect the result, especially for transforms.

Implementation support should be checked against the browsers required by a project rather than inferred from the draft’s existence. When unsupported, the declaration is ignored and the initial `replace` behavior remains, so provide an acceptable fallback and test the actual combinations you use. An `@supports (animation-composition: add)` query can be useful for progressive enhancement.

Further reading: [CSS Animations Level 2 — `animation-composition`](https://drafts.csswg.org/css-animations-2/#animation-composition)
