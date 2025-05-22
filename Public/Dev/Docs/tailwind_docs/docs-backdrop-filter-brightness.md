# https://tailwindcss.com/docs/backdrop-filter-brightness

[Original link](https://tailwindcss.com/docs/backdrop-filter-brightness)

## Examples

### Basic example

Use utilities likebackdrop-brightness-50andbackdrop-brightness-100to control an element's backdrop brightness:

backdrop-brightness-50

backdrop-brightness-150

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-brightness-50 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-brightness-150 ..."></div></div>
```

### Using a custom value

Use thebackdrop-brightness-[<value>]syntaxto set thebackdrop brightnessbased on a completely custom value:

```
<div class="backdrop-brightness-[1.75] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-brightness-(<custom-property>)syntax:

```
<div class="backdrop-brightness-(--my-backdrop-brightness) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-brightness-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: brightness()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-brightness-110 md:backdrop-brightness-150 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
