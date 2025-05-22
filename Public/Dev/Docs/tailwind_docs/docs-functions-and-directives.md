# https://tailwindcss.com/docs/functions-and-directives

[Original link](https://tailwindcss.com/docs/functions-and-directives)

## Directives

Directives are custom Tailwind-specificat-rulesyou can use in your CSS that offer special functionality for Tailwind CSS projects.

### @import

Use the@importdirective to inline import CSS files, including Tailwind itself:

```
@import "tailwindcss";
```

### @theme

Use the@themedirective to define your project's custom design tokens, like fonts, colors, and breakpoints:

```
@theme {  --font-display: "Satoshi", "sans-serif";  --breakpoint-3xl: 120rem;  --color-avocado-100: oklch(0.99 0 0);  --color-avocado-200: oklch(0.98 0.04 113.22);  --color-avocado-300: oklch(0.94 0.11 115.03);  --color-avocado-400: oklch(0.92 0.19 114.08);  --color-avocado-500: oklch(0.84 0.18 117.33);  --color-avocado-600: oklch(0.53 0.12 118.34);  --ease-fluid: cubic-bezier(0.3, 0, 0, 1);  --ease-snappy: cubic-bezier(0.2, 0, 0, 1);  /* ... */}
```

Learn more about customizing your theme in thetheme variables documentation.

### @source

Use the@sourcedirective to explicitly specify source files that aren't picked up by Tailwind's automatic content detection:

```
@source "../node_modules/@my-company/ui-lib";
```

Learn more about automatic content detection in thedetecting classes in source files documentation.

### @utility

Use the@utilitydirective to add custom utilities to your project that work with variants likehover,focusandlg:

```
@utility tab-4 {  tab-size: 4;}
```

Learn more about registering custom utilities in theadding custom utilities documentation.

### @variant

Use the@variantdirective to apply a Tailwind variant to styles in your CSS:

```
.my-element {  background: white;  @variant dark {    background: black;  }}
```

Learn more using variants in theusing variants documentation.

### @custom-variant

Use the@custom-variantdirective to add a custom variant in your project:

```
@custom-variant theme-midnight (&:where([data-theme="midnight"] *));
```

This lets you write utilitiestheme-midnight:bg-blackandtheme-midnight:text-white.

Learn more about adding custom variants in theadding custom variants documentation.

### @apply

Use the@applydirective to inline any existing utility classes into your own custom CSS:

```
.select2-dropdown {  @apply rounded-b-lg shadow-md;}.select2-search {  @apply rounded border border-gray-300;}.select2-results__group {  @apply text-lg font-bold text-gray-900;}
```

This is useful when you need to write custom CSS (like to override the styles in a third-party library) but still want to work with your design tokens and use the same syntax you’re used to using in your HTML.

### @reference

If you want to use@applyor@variantin the<style>block of a Vue or Svelte component, or within CSS modules, you will need to import your theme variables, custom utilities, and custom variants to make those values available in that context.

To do this without duplicating any CSS in your output, use the@referencedirective to import your main stylesheet for reference without actually including the styles:

```
<template>  <h1>Hello world!</h1></template><style>  @reference "../../app.css";  h1 {    @apply text-2xl font-bold text-red-500;  }</style>
```

If you’re just using the default theme with no customizations, you can importtailwindcssdirectly:

```
<template>  <h1>Hello world!</h1></template><style>  @reference "tailwindcss";  h1 {    @apply text-2xl font-bold text-red-500;  }</style>
```

## Functions

Tailwind provides the following build-time functions to make working with colors and the spacing scale easier.

### --alpha()

Use the--alpha()function to adjust the opacity of a color:

```
.my-element {  color: --alpha(var(--color-lime-300) / 50%);}
```

```
.my-element {  color: color-mix(in oklab, var(--color-lime-300) 50%, transparent);}
```

### --spacing()

Use the--spacing()function to generate a spacing value based on your theme:

```
.my-element {  margin: --spacing(4);}
```

```
.my-element {  margin: calc(var(--spacing) * 4);}
```

This can also be useful in arbitrary values, especially in combination withcalc():

```
<div class="py-[calc(--spacing(4)-1px)]">  <!-- ... --></div>
```

## Compatibility

The following directives and functions exist solely for compatibility with Tailwind CSS v3.x.

### @config

Use the@configdirective to load a legacy JavaScript-based configuration file:

```
@config "../../tailwind.config.js";
```

ThecorePlugins,safelist, andseparatoroptions from the JavaScript-based config are not supported in v4.0.

### @plugin

Use the@plugindirective to load a legacy JavaScript-based plugin:

```
@plugin "@tailwindcss/typography";
```

The@plugindirective accepts either a package name or a local path.

### theme()

Use thetheme()function to access your Tailwind theme values using dot notation:

```
.my-element {  margin: theme(spacing.12);}
```

This function is deprecated, and we recommendusing CSS theme variablesinstead.
