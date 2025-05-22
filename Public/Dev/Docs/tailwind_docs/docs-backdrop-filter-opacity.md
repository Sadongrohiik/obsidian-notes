# https://tailwindcss.com/docs/backdrop-filter-opacity

[Original link](https://tailwindcss.com/docs/backdrop-filter-opacity)

## Examples

### Basic example

Use utilities likebackdrop-opacity-50andbackdrop-opacity-75to control the opacity of all the backdrop filters applied to an element:

backdrop-opacity-10

backdrop-opacity-60

backdrop-opacity-95

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-invert backdrop-opacity-10 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-invert backdrop-opacity-60 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-invert backdrop-opacity-95 ..."></div></div>
```

### Using a custom value

Use thebackdrop-opacity-[<value>]syntaxto set thebackdrop filter opacitybased on a completely custom value:

```
<div class="backdrop-opacity-[.15] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-opacity-(<custom-property>)syntax:

```
<div class="backdrop-opacity-(--my-backdrop-filter-opacity) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-opacity-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: opacity()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-opacity-100 md:backdrop-opacity-60 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
