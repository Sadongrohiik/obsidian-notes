# https://tailwindcss.com/docs/backdrop-filter-contrast

[Original link](https://tailwindcss.com/docs/backdrop-filter-contrast)

## Examples

### Basic example

Use utilities likebackdrop-contrast-50andbackdrop-contrast-100to control an element's backdrop contrast:

backdrop-contrast-50

backdrop-contrast-200

```
<div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-contrast-50 ..."></div></div><div class="bg-[url(/img/mountains.jpg)]">  <div class="bg-white/30 backdrop-contrast-200 ..."></div></div>
```

### Using a custom value

Use thebackdrop-contrast-[<value>]syntaxto set thebackdrop contrastbased on a completely custom value:

```
<div class="backdrop-contrast-[.25] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-contrast-(<custom-property>)syntax:

```
<div class="backdrop-contrast-(--my-backdrop-contrast) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-contrast-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackdrop-filter: contrast()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-contrast-125 md:backdrop-contrast-150 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
