# https://tailwindcss.com/docs/stroke

[Original link](https://tailwindcss.com/docs/stroke)

## Examples

### Basic example

Use utilities likestroke-indigo-500andstroke-lime-600to change the stroke color of an SVG:

```
<svg class="stroke-cyan-500 ...">  <!-- ... --></svg>
```

This can be useful for styling icon sets likeHeroicons.

### Using the current color

Use thestroke-currentutility to set the stroke color to the current text color:

Hover over the button to see the stroke color change

```
<button class="bg-white text-pink-600 hover:bg-pink-600 hover:text-white ...">  <svg class="size-5 stroke-current ..." fill="none">    <!-- ... -->  </svg>  Download file</button>
```

### Using a custom value

Use thestroke-[<value>]syntaxto set thestroke colorbased on a completely custom value:

```
<svg class="stroke-[#243c5a] ...">  <!-- ... --></svg>
```

For CSS variables, you can also use thestroke-(<custom-property>)syntax:

```
<svg class="stroke-(--my-stroke-color) ...">  <!-- ... --></svg>
```

This is just a shorthand forstroke-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixastrokeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<svg class="stroke-cyan-500 md:stroke-cyan-700 ...">  <!-- ... --></svg>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thestroke-regal-blueutility can be used in your markup:

```
<svg class="stroke-regal-blue">  <!-- ... --></svg>
```

Learn more about customizing your theme in thetheme documentation.
