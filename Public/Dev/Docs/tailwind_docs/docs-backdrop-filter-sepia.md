# https://tailwindcss.com/docs/backdrop-filter-sepia

[Original link](https://tailwindcss.com/docs/backdrop-filter-sepia)

## Examples

### Basic example

Use utilities likebackdrop-sepiaandbackdrop-sepia-50to control the sepia effect applied to an element's backdrop:

backdrop-sepia-0

backdrop-sepia-50

backdrop-sepia

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-sepia-0 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-sepia-50 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-sepia ..."></div></div>
```

### Using a custom value

Use thebackdrop-sepia-[<value>]syntaxto set thebackdrop sepiabased on a completely custom value:

```
<div class="backdrop-sepia-[.25] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-sepia-(<custom-property>)syntax:

```
<div class="backdrop-sepia-(--my-backdrop-sepia) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-sepia-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: sepia()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-sepia md:backdrop-sepia-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
