# https://tailwindcss.com/docs/adding-custom-styles

[Original link](https://tailwindcss.com/docs/adding-custom-styles)

Often the biggest challenge when working with a framework is figuring out what you’re supposed to do when there’s something you need that the framework doesn’t handle for you.

Tailwind has been designed from the ground up to be extensible and customizable, so that no matter what you’re building you never feel like you’re fighting the framework.

This guide covers topics like customizing your design tokens, how to break out of those constraints when necessary, adding your own custom CSS, and extending the framework with plugins.

## Customizing your theme

If you want to change things like your color palette, spacing scale, typography scale, or breakpoints, add your customizations using the@themedirective in your CSS:

```
@theme {  --font-display: "Satoshi", "sans-serif";  --breakpoint-3xl: 120rem;  --color-avocado-100: oklch(0.99 0 0);  --color-avocado-200: oklch(0.98 0.04 113.22);  --color-avocado-300: oklch(0.94 0.11 115.03);  --color-avocado-400: oklch(0.92 0.19 114.08);  --color-avocado-500: oklch(0.84 0.18 117.33);  --color-avocado-600: oklch(0.53 0.12 118.34);  --ease-fluid: cubic-bezier(0.3, 0, 0, 1);  --ease-snappy: cubic-bezier(0.2, 0, 0, 1);  /* ... */}
```

Learn more about customizing your theme in thetheme variables documentation.

## Using arbitrary values

While you can usually build the bulk of a well-crafted design using a constrained set of design tokens, once in a while you need to break out of those constraints to get things pixel-perfect.

When you find yourself really needing something liketop: 117pxto get a background image in just the right spot, use Tailwind's square bracket notation to generate a class on the fly with any arbitrary value:

```
<div class="top-[117px]">  <!-- ... --></div>
```

This is basically like inline styles, with the major benefit that you can combine it with interactive modifiers likehoverand responsive modifiers likelg:

```
<div class="top-[117px] lg:top-[344px]">  <!-- ... --></div>
```

This works for everything in the framework, including things like background colors, font sizes, pseudo-element content, and more:

```
<div class="bg-[#bada55] text-[22px] before:content-['Festivus']">  <!-- ... --></div>
```

If you're referencing a CSS variable as an arbitrary value, you can use the custom property syntax:

```
<div class="fill-(--my-brand-color) ...">  <!-- ... --></div>
```

This is just a shorthand forfill-[var(--my-brand-color)]that adds thevar()function for you automatically.

### Arbitrary properties

If you ever need to use a CSS property that Tailwind doesn't include a utility for out of the box, you can also use square bracket notation to write completely arbitrary CSS:

```
<div class="[mask-type:luminance]">  <!-- ... --></div>
```

This isreallylike inline styles, but again with the benefit that you can use modifiers:

```
<div class="[mask-type:luminance] hover:[mask-type:alpha]">  <!-- ... --></div>
```

This can be useful for things like CSS variables as well, especially when they need to change under different conditions:

```
<div class="[--scroll-offset:56px] lg:[--scroll-offset:44px]">  <!-- ... --></div>
```

### Arbitrary variants

Arbitraryvariantsare like arbitrary values but for doing on-the-fly selector modification, like you can with built-in pseudo-class variants likehover:{utility}or responsive variants likemd:{utility}but using square bracket notation directly in your HTML.

```
<ul role="list">  {#each items as item}  <li class="lg:[&:nth-child(-n+3)]:hover:underline">{item}</li>  {/each}</ul>
```

Learn more in thearbitrary variantsdocumentation.

### Handling whitespace

When an arbitrary value needs to contain a space, use an underscore (_) instead and Tailwind will automatically convert it to a space at build-time:

```
<div class="grid grid-cols-[1fr_500px_2fr]">  <!-- ... --></div>
```

In situations where underscores are common but spaces are invalid, Tailwind will preserve the underscore instead of converting it to a space, for example in URLs:

```
<div class="bg-[url('/what_a_rush.png')]">  <!-- ... --></div>
```

In the rare case that you actually need to use an underscore but it's ambiguous because a space is valid as well, escape the underscore with a backslash and Tailwind won't convert it to a space:

```
<div class="before:content-['hello\_world']">  <!-- ... --></div>
```

If you're using something like JSX where the backslash is stripped from the rendered HTML, useString.raw()so the backslash isn't treated as a JavaScript escape character:

```
<div className={String.raw`before:content-['hello\_world']`}>  <!-- ... --></div>
```

### Resolving ambiguities

Many utilities in Tailwind share a common namespace but map to different CSS properties. For exampletext-lgandtext-blackboth share thetext-namespace, but one is forfont-sizeand the other is forcolor.

When using arbitrary values, Tailwind can generally handle this ambiguity automatically based on the value you pass in:

```
<!-- Will generate a font-size utility --><div class="text-[22px]">...</div><!-- Will generate a color utility --><div class="text-[#bada55]">...</div>
```

Sometimes it really is ambiguous though, for example when using CSS variables:

```
<div class="text-(--my-var)">...</div>
```

In these situations, you can "hint" the underlying type to Tailwind by adding aCSS data typebefore the value:

```
<!-- Will generate a font-size utility --><div class="text-(length:--my-var)">...</div><!-- Will generate a color utility --><div class="text-(color:--my-var)">...</div>
```

## Using custom CSS

While Tailwind is designed to handle the bulk of your styling needs, there is nothing stopping you from just writing plain CSS when you need to:

```
@import "tailwindcss";.my-custom-style {  /* ... */}
```

### Adding base styles

If you just want to set some defaults for the page (like the text color, background color, or font family), the easiest option is just adding some classes to thehtmlorbodyelements:

```
<!doctype html><html lang="en" class="bg-gray-100 font-serif text-gray-900">  <!-- ... --></html>
```

This keeps your base styling decisions in your markup alongside all of your other styles, instead of hiding them in a separate file.

If you want to add your own default base styles for specific HTML elements, use the@layerdirective to add those styles to Tailwind'sbaselayer:

```
@layer base {  h1 {    font-size: var(--text-2xl);  }  h2 {    font-size: var(--text-xl);  }}
```

### Adding component classes

Use thecomponentslayer for any more complicated classes you want to add to your project that you'd still like to be able to override with utility classes.

Traditionally these would be classes likecard,btn,badge— that kind of thing.

```
@layer components {  .card {    background-color: var(--color-white);    border-radius: var(--rounded-lg);    padding: var(--spacing-6);    box-shadow: var(--shadow-xl);  }}
```

By defining component classes in thecomponentslayer, you can still use utility classes to override them when necessary:

```
<!-- Will look like a card, but with square corners --><div class="card rounded-none">  <!-- ... --></div>
```

Using Tailwind you probably don't need these types of classes as often as you think. Read our guide onmanaging duplicationfor our recommendations.

Thecomponentslayer is also a good place to put custom styles for any third-party components you're using:

```
@layer components {  .select2-dropdown {    /* ... */  }}
```

### Using variants

Use the@variantdirective to apply a Tailwind variant within custom CSS:

```
.my-element {  background: white;  @variant dark {    background: black;  }}
```

```
.my-element {  background: white;  @media (prefers-color-scheme: dark) {    background: black;  }}
```

If you need to apply multiple variants at the same time, use nesting:

```
.my-element {  background: white;  @variant dark {    @variant hover {      background: black;    }  }}
```

```
.my-element {  background: white;  @media (prefers-color-scheme: dark) {    &:hover {      @media (hover: hover) {        background: black;      }    }  }}
```

## Adding custom utilities

### Simple utilities

In addition to using the utilities that ship with Tailwind, you can also add your own custom utilities. This can be useful when there's a CSS feature you'd like to use in your project that Tailwind doesn't include utilities for out of the box.

Use the@utilitydirective to add a custom utility to your project:

```
@utility content-auto {  content-visibility: auto;}
```

You can now use this utility in your HTML:

```
<div class="content-auto">  <!-- ... --></div>
```

It will also work with variants likehover,focusandlg:

```
<div class="hover:content-auto">  <!-- ... --></div>
```

Custom utilities are automatically inserted into theutilitieslayer along with all of the built-in utilities in the framework.

### Complex utilities

If your custom utility is more complex than a single class name, use nesting to define the utility:

```
@utility scrollbar-hidden {  &::-webkit-scrollbar {    display: none;  }}
```

### Functional utilities

In addition to registering simple utilities with the@utilitydirective, you can also register functional utilities that accept an argument:

```
@utility tab-* {  tab-size: --value(--tab-size-*);}
```

The special--value()function is used to resolve the utility value.

#### Matching theme values

Use the--value(--theme-key-*)syntax to resolve the utility value against a set of theme keys:

```
@theme {  --tab-size-2: 2;  --tab-size-4: 4;  --tab-size-github: 8;}@utility tab-* {  tab-size: --value(--tab-size-*);}
```

This will match utilities liketab-2,tab-4, andtab-github.

#### Bare values

To resolve the value as a bare value, use the--value({type})syntax, where{type}is the data type you want to validate the bare value as:

```
@utility tab-* {  tab-size: --value(integer);}
```

This will match utilities liketab-1andtab-76.

#### Literal values

To support literal values, use the--value('literal')syntax (notice the quotes):

```
@utility tab-* {  tab-size: --value('inherit', 'initial', 'unset');}
```

This will match utilities liketab-inherit,tab-initial, andtab-unset.

#### Arbitrary values

To support arbitrary values, use the--value([{type}])syntax (notice the square brackets) to tell Tailwind which types are supported as an arbitrary value:

```
@utility tab-* {  tab-size: --value([integer]);}
```

This will match utilities liketab-[1]andtab-[76]. If you want to support any data type, you can use--value([*]).

#### Supporting theme, bare, and arbitrary values together

All three forms of the--value()function can be used within a rule as multiple declarations, and any declarations that fail to resolve will be omitted in the output:

```
@theme {  --tab-size-github: 8;}@utility tab-* {  tab-size: --value([integer]);  tab-size: --value(integer);  tab-size: --value(--tab-size-*);}
```

This makes it possible to treat the value differently in each case if necessary, for example translating a bare integer to a percentage:

```
@utility opacity-* {  opacity: --value([percentage]);  opacity: calc(--value(integer) * 1%);  opacity: --value(--opacity-*);}
```

The--value()function can also take multiple arguments and resolve them left to right if you don't need to treat the return value differently in different cases:

```
@theme {  --tab-size-github: 8;}@utility tab-* {  tab-size: --value(--tab-size-*, integer, [integer]);}@utility opacity-* {  opacity: calc(--value(integer) * 1%);  opacity: --value(--opacity-*, [percentage]);}
```

#### Negative values

To support negative values, register separate positive and negative utilities into separate declarations:

```
@utility inset-* {  inset: calc(var(--spacing) * --value([percentage], [length]));}@utility -inset-* {  inset: calc(var(--spacing) * --value([percentage], [length]) * -1);}
```

#### Modifiers

Modifiers are handled using the--modifier()function which works exactly like the--value()function but operates on a modifier if present:

```
@utility text-* {  font-size: --value(--text-*, [length]);  line-height: --modifier(--leading-*, [length], [*]);}
```

If a modifier isn't present, any declaration depending on a modifier is just not included in the output.

#### Fractions

To handle fractions, we rely on the CSSratiodata type. If this is used with--value(), it's a signal to Tailwind to treat the value and modifier as a single value:

```
@utility aspect-* {  aspect-ratio: --value(--aspect-ratio-*, ratio, [ratio]);}
```

This will match utilities likeaspect-square,aspect-3/4, andaspect-[7/9].

## Adding custom variants

In addition to using the variants that ship with Tailwind, you can also add your own custom variants using the@custom-variantdirective:

```
@custom-variant theme-midnight {  &:where([data-theme="midnight"] *) {    @slot;  }}
```

Now you can use thetheme-midnight:<utility>variant in your HTML:

```
<html data-theme="midnight">  <button class="theme-midnight:bg-black ..."></button></html>
```

You can create variants using the shorthand syntax when nesting isn't required:

```
@custom-variant theme-midnight (&:where([data-theme="midnight"] *));
```

When a custom variant has multiple rules, they can be nested within each other:

```
@custom-variant any-hover {  @media (any-hover: hover) {    &:hover {      @slot;    }  }}
```
