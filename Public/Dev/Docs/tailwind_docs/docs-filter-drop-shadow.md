# https://tailwindcss.com/docs/filter-drop-shadow

[Original link](https://tailwindcss.com/docs/filter-drop-shadow)

## Examples

### Basic example

Use utilities likedrop-shadow-smanddrop-shadow-xlto add a drop shadow to an element:

drop-shadow-md

drop-shadow-lg

drop-shadow-xl

```
<svg class="drop-shadow-md ...">  <!-- ... --></svg><svg class="drop-shadow-lg ...">  <!-- ... --></svg><svg class="drop-shadow-xl ...">  <!-- ... --></svg>
```

This is useful for applying shadows to irregular shapes, like text and SVG elements. For applying shadows to regular elements, you probably want to usebox shadowinstead.

### Changing the opacity

Use the opacity modifier to adjust the opacity of the drop shadow:

drop-shadow-xl

drop-shadow-xl/25

drop-shadow-xl/50

```
<svg class="fill-white drop-shadow-xl ...">...</svg><svg class="fill-white drop-shadow-xl/25 ...">...</svg><svg class="fill-white drop-shadow-xl/50 ...">...</svg>
```

The default drop shadow opacities are quite low (15% or less), so increasing the opacity (to like 50%) will make the drop shadows more pronounced.

### Setting the shadow color

Use utilities likedrop-shadow-indigo-500anddrop-shadow-cyan-500/50to change the color of a drop shadow:

drop-shadow-cyan-500/50

drop-shadow-indigo-500/50

```
<svg class="fill-cyan-500 drop-shadow-lg drop-shadow-cyan-500/50 ...">...</svg><svg class="fill-indigo-500 drop-shadow-lg drop-shadow-indigo-500/50 ...">...</svg>
```

By default colored shadows have an opacity of 100% but you can adjust this using the opacity modifier.

### Removing a drop shadow

Use thedrop-shadow-noneutility to remove an existing drop shadow from an element:

```
<svg class="drop-shadow-lg dark:drop-shadow-none">  <!-- ... --></svg>
```

### Using a custom value

Use thedrop-shadow-[<value>]syntaxto set thedrop shadowbased on a completely custom value:

```
<svg class="drop-shadow-[0_35px_35px_rgba(0,0,0,0.25)] ...">  <!-- ... --></svg>
```

For CSS variables, you can also use thedrop-shadow-(<custom-property>)syntax:

```
<svg class="drop-shadow-(--my-drop-shadow) ...">  <!-- ... --></svg>
```

This is just a shorthand fordrop-shadow-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: drop-shadow()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<svg class="drop-shadow-md md:drop-shadow-xl ...">  <!-- ... --></svg>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

### Customizing drop shadows

Use the--drop-shadow-*theme variables to customize thedrop shadowutilities in your project:

```
@theme {  --drop-shadow-3xl: 0 35px 35px rgba(0, 0, 0, 0.25); }
```

Now thedrop-shadow-3xlutility can be used in your markup:

```
<svg class="drop-shadow-3xl">  <!-- ... --></svg>
```

Learn more about customizing your theme in thetheme documentation.

### Customizing shadow colors

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thedrop-shadow-regal-blueutility can be used in your markup:

```
<svg class="drop-shadow-regal-blue">  <!-- ... --></svg>
```

Learn more about customizing your theme in thetheme documentation.
