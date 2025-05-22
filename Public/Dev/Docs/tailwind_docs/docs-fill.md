# https://tailwindcss.com/docs/fill

[Original link](https://tailwindcss.com/docs/fill)

## Examples

### Basic example

Use utilities likefill-indigo-500andfill-lime-600to change the fill color of an SVG:

```
<svg class="fill-blue-500 ...">  <!-- ... --></svg>
```

This can be useful for styling icon sets likeHeroicons.

### Using the current color

Use thefill-currentutility to set the fill color to the current text color:

Hover over the button to see the fill color change

```
<button class="bg-white text-indigo-600 hover:bg-indigo-600 hover:text-white ...">  <svg class="size-5 fill-current ...">    <!-- ... -->  </svg>  Check for updates</button>
```

### Using a custom value

Use thefill-[<value>]syntaxto set thefill colorbased on a completely custom value:

```
<svg class="fill-[#243c5a] ...">  <!-- ... --></svg>
```

For CSS variables, you can also use thefill-(<custom-property>)syntax:

```
<svg class="fill-(--my-fill-color) ...">  <!-- ... --></svg>
```

This is just a shorthand forfill-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafillutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<svg class="fill-cyan-500 md:fill-cyan-700 ...">  <!-- ... --></svg>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thefill-regal-blueutility can be used in your markup:

```
<svg class="fill-regal-blue">  <!-- ... --></svg>
```

Learn more about customizing your theme in thetheme documentation.
