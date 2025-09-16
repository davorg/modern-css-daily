---
title: "font-display"
date: 2025-09-16
categories: ["CSS"]
tags: [font-display]
layout: single
---

Introduced in the CSS Fonts Module Level 4 specification, "font-display" is a vital property for web developers who aim to enhance the performance and aesthetics of their websites. This property allows developers to specify how downloadable web fonts are displayed on the browser, accommodating different states of font loading. Traditionally, when a custom font is used on a webpage, there might be a small delay before it is displayed. During this period, users might experience a flash of invisible text (FOIT) or a flash of unstyled text (FOUT). "font-display" offers a way to control this behavior.

The "font-display" property has five possible values: auto, block, swap, fallback, and optional. Here's what each does:
- **auto**: This is the default behavior and allows the browser to decide how to display the font.
- **block**: The browser hides the text (FOIT) until the font is fully downloaded. There's a short block period (usually 3 seconds) followed by a swap period.
- **swap**: This ensures that fallback fonts are displayed immediately (FOUT) and swapped out once the custom font is fully loaded.
- **fallback**: Similar to block, but if the font is not loaded within a short period, it remains with the fallback font.
- **optional**: If the font isn’t loaded quickly, the fallback font remains, and the custom font might not be swapped in even after loading.

Here's an example of how you might use "font-display" in your CSS:

```css
@font-face {
  font-family: 'OpenSans';
  src: url('/fonts/OpenSans.woff2') format('woff2'),
       url('/fonts/OpenSans.woff') format('woff');
  font-display: swap;
}
```

In this example, "font-display: swap" ensures that the text is readable immediately with a fallback font and is seamlessly replaced by 'OpenSans' once it loads. 

The usefulness of "font-display" cannot be understated in today's web development landscape. Producing a faster perceived load time, improving accessibility, and enhancing the user experience, it empowers developers to manage font loading decisions previously left to the browser's discretion.

However, developers should be aware that while most modern browsers support "font-display," there might be discrepancies in how it's implemented. As of the latest updates, the property is well-supported in Chrome, Firefox, Edge, and Safari 11.1 and later. Internet Explorer, unsurprisingly, does not support it, which might necessitate additional handling for backward compatibility.

In conclusion, "font-display" is a must-know feature for web developers looking to fine-tune their site's typography performance. By strategically employing it, developers can ensure that text remains legible during font loading, producing a superior browsing experience.
