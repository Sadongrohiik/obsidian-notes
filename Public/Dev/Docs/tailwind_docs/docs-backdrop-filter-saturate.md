# https://tailwindcss.com/docs/backdrop-filter-saturate

[Original link](https://tailwindcss.com/docs/backdrop-filter-saturate)

## Examples

### Basic example

Use utilities likebackdrop-saturate-50andbackdrop-saturate-100utilities to control the saturation of an element's backdrop:

backdrop-saturate-50

backdrop-saturate-125

backdrop-saturate-200

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-saturate-50 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-saturate-125 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-saturate-200 ..."></div></div>
```

### Using a custom value

Use thebackdrop-saturate-[<value>]syntaxto set thebackdrop saturationbased on a completely custom value:

```
<div class="backdrop-saturate-[.25] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-saturate-(<custom-property>)syntax:

```
<div class="backdrop-saturate-(--my-backdrop-saturation) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-saturate-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: saturate()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-saturate-50 md:backdrop-saturate-150 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
