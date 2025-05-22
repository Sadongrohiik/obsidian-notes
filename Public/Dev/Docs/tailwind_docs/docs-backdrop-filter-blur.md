# https://tailwindcss.com/docs/backdrop-filter-blur

[Original link](https://tailwindcss.com/docs/backdrop-filter-blur)

## Examples

### Basic example

Use utilities likebackdrop-blur-smandbackdrop-blur-lgto control an element’s backdrop blur:

backdrop-blur-none

backdrop-blur-sm

backdrop-blur-md

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-blur-none ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-blur-sm ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-blur-md ..."></div></div>
```

### Using a custom value

Use thebackdrop-blur-[<value>]syntaxto set thebackdrop blurbased on a completely custom value:

```
<div class="backdrop-blur-[2px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-blur-(<custom-property>)syntax:

```
<div class="backdrop-blur-(--my-backdrop-blur) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-blur-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: blur()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-blur-none md:backdrop-blur-lg ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--blur-*theme variables to customize thebackdrop blurutilities in your project:

```
@theme {  --blur-2xs: 2px; }
```

Now thebackdrop-blur-2xsutility can be used in your markup:

```
<div class="backdrop-blur-2xs">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
