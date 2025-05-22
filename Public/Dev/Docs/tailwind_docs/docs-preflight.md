# https://tailwindcss.com/docs/preflight

[Original link](https://tailwindcss.com/docs/preflight)

## Overview

Built on top ofmodern-normalize, Preflight is a set of base styles for Tailwind projects that are designed to smooth over cross-browser inconsistencies and make it easier for you to work within the constraints of your design system.

When you importtailwindcssinto your project, Preflight is automatically injected into thebaselayer:

```
@layer theme, base, components, utilities;@import "tailwindcss/theme.css" layer(theme);@import "tailwindcss/preflight.css" layer(base);@import "tailwindcss/utilities.css" layer(utilities);
```

While most of the styles in Preflight are meant to go unnoticed—they simply make things behave more like you'd expect them to—some are more opinionated and can be surprising when you first encounter them.

For a complete reference of all the styles applied by Preflight,see the stylesheet.

### Margins are removed

Preflight removes all of the default margins from all elements including headings, blockquotes, paragraphs, etc:

```
*,::after,::before,::backdrop,::file-selector-button {  margin: 0;  padding: 0;}
```

This makes it harder to accidentally rely on margin values applied by the user-agent stylesheet that are not part of your spacing scale.

### Border styles are reset

In order to make it easy to add a border by simply adding theborderclass, Tailwind overrides the default border styles for all elements with the following rules:

```
*,::after,::before,::backdrop,::file-selector-button {  box-sizing: border-box;  border: 0 solid;}
```

Since theborderclass only sets theborder-widthproperty, this reset ensures that adding that class always adds a solid1pxborder that usescurrentColor.

This can cause some unexpected results when integrating certain third-party libraries, likeGoogle mapsfor example.

When you run into situations like this, you can work around them by overriding the Preflight styles with your own custom CSS:

```
@layer base {  .google-map * {    border-style: none;  }}
```

### Headings are unstyled

All heading elements are completely unstyled by default, and have the same font size and weight as normal text:

```
h1,h2,h3,h4,h5,h6 {  font-size: inherit;  font-weight: inherit;}
```

The reason for this is two-fold:

You can always add default header styles to your project byadding your own base styles.

### Lists are unstyled

Ordered and unordered lists are unstyled by default, with no bullets or numbers:

```
ol,ul,menu {  list-style: none;}
```

If you'd like to style a list, you can do so using thelist-style-typeandlist-style-positionutilities:

```
<ul class="list-inside list-disc">  <li>One</li>  <li>Two</li>  <li>Three</li></ul>
```

You can always add default list styles to your project byadding your own base styles.

#### Accessibility considerations

Unstyled lists arenot announced as lists by VoiceOver. If your content is truly a list but you would like to keep it unstyled,add a "list" roleto the element:

```
<ul role="list">  <li>One</li>  <li>Two</li>  <li>Three</li></ul>
```

### Images are block-level

Images and other replaced elements (likesvg,video,canvas, and others) aredisplay: blockby default:

```
img,svg,video,canvas,audio,iframe,embed,object {  display: block;  vertical-align: middle;}
```

This helps to avoid unexpected alignment issues that you often run into using the browser default ofdisplay: inline.

If you ever need to make one of these elementsinlineinstead ofblock, simply use theinlineutility:

```
<img class="inline" src="..." alt="..." />
```

### Images are constrained

Images and videos are constrained to the parent width in a way that preserves their intrinsic aspect ratio:

```
img,video {  max-width: 100%;  height: auto;}
```

This prevents them from overflowing their containers and makes them responsive by default. If you ever need to override this behavior, use themax-w-noneutility:

```
<img class="max-w-none" src="..." alt="..." />
```

## Extending Preflight

If you'd like to add your own base styles on top of Preflight, add them to thebaseCSS layer in your CSS using@layer base:

```
@layer base {  h1 {    font-size: var(--text-2xl);  }  h2 {    font-size: var(--text-xl);  }  h3 {    font-size: var(--text-lg);  }  a {    color: var(--color-blue-600);    text-decoration-line: underline;  }}
```

Learn more in theadding base styles documentation.

## Disabling Preflight

If you'd like to completely disable Preflight—perhaps because you're integrating Tailwind into an existing project or you'd prefer to define your own base styles—you can do so by importing only the parts of Tailwind that you need.

By default, this is what@import "tailwindcss";injects:

```
@layer theme, base, components, utilities;@import "tailwindcss/theme.css" layer(theme);@import "tailwindcss/preflight.css" layer(base);@import "tailwindcss/utilities.css" layer(utilities);
```

To disable Preflight, simply omit its import while keeping everything else:

```
@layer theme, base, components, utilities;@import "tailwindcss/theme.css" layer(theme);@import "tailwindcss/preflight.css" layer(base);@import "tailwindcss/utilities.css" layer(utilities);
```
