# https://tailwindcss.com/docs/stroke-width

[Original link](https://tailwindcss.com/docs/stroke-width)

## Examples

### Basic example

Usestroke-<number>utilities likestroke-1andstroke-2to set the stroke width of an SVG:

```
<svg class="stroke-1 ..."></svg><svg class="stroke-2 ..."></svg>
```

This can be useful for styling icon sets likeHeroicons.

### Using a custom value

Use thestroke-[<value>]syntaxto set thestroke widthbased on a completely custom value:

```
<div class="stroke-[1.5] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thestroke-(length:<custom-property>)syntax:

```
<div class="stroke-(length:--my-stroke-width) ...">  <!-- ... --></div>
```

This is just a shorthand forstroke-[length:var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixastroke-widthutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="stroke-1 md:stroke-2 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
