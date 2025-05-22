# https://tailwindcss.com/docs/backdrop-filter-invert

[Original link](https://tailwindcss.com/docs/backdrop-filter-invert)

## Examples

### Basic example

Use utilities likebackdrop-invertandbackdrop-invert-65to control the color inversion of an element's backdrop:

backdrop-invert-0

backdrop-invert-65

backdrop-invert

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-invert-0 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-invert-65 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-invert ..."></div></div>
```

### Using a custom value

Use thebackdrop-invert-[<value>]syntaxto set thebackdrop inversionbased on a completely custom value:

```
<div class="backdrop-invert-[.25] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-invert-(<custom-property>)syntax:

```
<div class="backdrop-invert-(--my-backdrop-inversion) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-invert-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: invert()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-invert-0 md:backdrop-invert ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
