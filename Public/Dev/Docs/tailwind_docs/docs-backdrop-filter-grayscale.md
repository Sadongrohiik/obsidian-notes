# https://tailwindcss.com/docs/backdrop-filter-grayscale

[Original link](https://tailwindcss.com/docs/backdrop-filter-grayscale)

## Examples

### Basic example

Use utilities likebackdrop-grayscale-50andbackdrop-grayscaleto control the grayscale effect applied to an element's backdrop:

backdrop-grayscale-0

backdrop-grayscale-50

backdrop-grayscale

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-grayscale-0 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-grayscale-50 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-grayscale-200 ..."></div></div>
```

### Using a custom value

Use thebackdrop-grayscale-[<value>]syntaxto set thebackdrop grayscalebased on a completely custom value:

```
<div class="backdrop-grayscale-[0.5] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-grayscale-(<custom-property>)syntax:

```
<div class="backdrop-grayscale-(--my-backdrop-grayscale) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-grayscale-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: grayscale()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-grayscale md:backdrop-grayscale-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
