# https://tailwindcss.com/docs/backdrop-filter

[Original link](https://tailwindcss.com/docs/backdrop-filter)

## Examples

### Basic example

Use utilities likebackdrop-blur-xsandbackdrop-grayscaleto apply filters to an element's backdrop:

backdrop-blur-xs

backdrop-grayscale

combined

```
<div class="bg-[url(/img/mountains.jpg)] ...">  <div class="backdrop-blur-xs ..."></div></div><div class="bg-[url(/img/mountains.jpg)] ...">  <div class="backdrop-grayscale ..."></div></div><div class="bg-[url(/img/mountains.jpg)] ...">  <div class="backdrop-blur-xs backdrop-grayscale ..."></div></div>
```

You can combine the following backdrop filter utilities:blur,brightness,contrast,grayscale,hue-rotate,invert,opacity,saturate, andsepia.

### Removing filters

Use thebackdrop-filter-noneutility to remove all of the backdrop filters applied to an element:

```
<div class="backdrop-blur-md backdrop-brightness-150 md:backdrop-filter-none"></div>
```

### Using a custom value

Use thebackdrop-filter-[<value>]syntaxto set thebackdrop filterbased on a completely custom value:

```
<div class="backdrop-filter-[url('filters.svg#filter-id')] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebackdrop-filter-(<custom-property>)syntax:

```
<div class="backdrop-filter-(--my-backdrop-filter) ...">  <!-- ... --></div>
```

This is just a shorthand forbackdrop-filter-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixabackdrop-filterutility with a variant likehover:*to only apply the utility in that state:

```
<div class="backdrop-blur-sm hover:backdrop-filter-none ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixabackdrop-filterutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="backdrop-blur-sm md:backdrop-filter-none ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
