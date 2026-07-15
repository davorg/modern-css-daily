---
title: "motion-preference"
date: 2026-07-15
categories: ["CSS"]
tags: [motion-preference]
layout: single
---

In recent years, as web design has evolved to include more animated and interactive elements, the need for accessible and user-centric design features has become increasingly important. One such feature is the CSS "motion-preference" media query, introduced to address users' varying preferences for motion on the web.

The "motion-preference" feature was introduced as part of the "prefers-reduced-motion" media query in the CSS Media Queries Level 5 specification, around 2017. This feature allows developers to determine if a user has indicated a preference for reduced motion in their system settings. This is particularly crucial for users who may experience motion sickness or have conditions such as vestibular disorders, which can be aggravated by complex or intense animations often found in modern web design.

The "prefers-reduced-motion" media query enables developers to tailor web experiences according to these user preferences. By querying this feature, developers can conditionally alter animations, transitions, or any motion-based content on their websites. Here's an example of how it might be used in practice:

```css
@media (prefers-reduced-motion: reduce) {
  .animated-element {
    animation: none;
    transition: none;
  }
}
```

In this example, when a user has indicated a preference for reduced motion, all animations and transitions for elements with the class `animated-element` are effectively disabled. This simple condition can significantly enhance the user experience by aligning the website's behavior with the user's comfort levels.

Today, the "motion-preference" feature is particularly useful as web animations become increasingly prevalent. It offers a way to respect users' needs without compromising the aesthetic or functional quality of a website for the majority. As digital environments grow more immersive, considering accessibility features like "motion-preference" isn't just about compliance; it's about empathy and inclusive design.

However, there are some caveats and considerations regarding browser support and implementation. As of now, "prefers-reduced-motion" is widely supported across modern browsers, including the latest versions of Chrome, Firefox, Safari, and Edge. It's essential, however, to conduct thorough testing across different environments to ensure consistent behavior. Additionally, because this is a user-configured setting, it only applies if users have set this preference at the system level, which may not always be the case.

Understanding and implementing "motion-preference" in your projects can be a key component in crafting accessible, user-friendly interfaces. By doing so, developers not only ensure compliance with best practices but also demonstrate a commitment to inclusive design principles that prioritize user well-being.
