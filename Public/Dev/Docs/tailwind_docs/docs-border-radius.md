# https://tailwindcss.com/docs/border-radius

[Original link](https://tailwindcss.com/docs/border-radius)

## Examples

### Basic example

Use utilities likerounded-smandrounded-mdto apply different border radius sizes to an element:

rounded-sm

rounded-md

rounded-lg

rounded-xl

```
<div class="rounded-sm ..."></div><div class="rounded-md ..."></div><div class="rounded-lg ..."></div><div class="rounded-xl ..."></div>
```

### Rounding sides separately

Use utilities likerounded-t-mdandrounded-r-lgto only round one side of an element:

rounded-t-lg

rounded-r-lg

rounded-b-lg

rounded-l-lg

```
<div class="rounded-t-lg ..."></div><div class="rounded-r-lg ..."></div><div class="rounded-b-lg ..."></div><div class="rounded-l-lg ..."></div>
```

### Rounding corners separately

Use utilities likerounded-tr-mdandrounded-tl-lgutilities to only round one corner of an element:

rounded-tl-lg

rounded-tr-lg

rounded-br-lg

rounded-bl-lg

```
<div class="rounded-tl-lg ..."></div><div class="rounded-tr-lg ..."></div><div class="rounded-br-lg ..."></div><div class="rounded-bl-lg ..."></div>
```

### Using logical properties

Use utilities likerounded-s-mdandrounded-se-xlto set the border radius usinglogical properties, which map to the appropriate corners based on the text direction:

Left-to-right

Right-to-left

```
<div dir="ltr">  <div class="rounded-s-lg ..."></div></div><div dir="rtl">  <div class="rounded-s-lg ..."></div></div>
```

Here are all the available border radius logical property utilities and their physical property equivalents in both LTR and RTL modes.

For more control, you can also use theLTR and RTL modifiersto conditionally apply specific styles depending on the current text direction.

### Creating pill buttons

Use therounded-fullutility to create pill buttons:

rounded-full

```
<button class="rounded-full ...">Save Changes</button>
```

### Removing the border radius

Use therounded-noneutility to remove an existing border radius from an element:

rounded-none

```
<button class="rounded-none ...">Save Changes</button>
```

### Using a custom value

Use therounded-[<value>]syntaxto set theborder radiusbased on a completely custom value:

```
<div class="rounded-[2vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use therounded-(<custom-property>)syntax:

```
<div class="rounded-(--my-radius) ...">  <!-- ... --></div>
```

This is just a shorthand forrounded-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaborder-radiusutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="rounded md:rounded-lg ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--radius-*theme variables to customize theborder radiusutilities in your project:

```
@theme {  --radius-5xl: 3rem; }
```

Now therounded-5xlutility can be used in your markup:

```
<div class="rounded-5xl">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
