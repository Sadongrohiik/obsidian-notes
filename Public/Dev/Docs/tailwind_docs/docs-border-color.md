# https://tailwindcss.com/docs/border-color

[Original link](https://tailwindcss.com/docs/border-color)

## Examples

### Basic example

Use utilities likeborder-rose-500andborder-lime-100to control the border color of an element:

border-indigo-500

border-purple-500

border-sky-500

```
<div class="border-4 border-indigo-500 ..."></div><div class="border-4 border-purple-500 ..."></div><div class="border-4 border-sky-500 ..."></div>
```

### Changing the opacity

Use the color opacity modifier to control the opacity of an element's border color:

border-indigo-500/100

border-indigo-500/75

border-indigo-500/50

```
<div class="border-4 border-indigo-500/100 ..."></div><div class="border-4 border-indigo-500/75 ..."></div><div class="border-4 border-indigo-500/50 ..."></div>
```

### Individual sides

Use utilities likeborder-t-indigo-500andborder-r-lime-100to set the border color for one side of an element:

border-t-indigo-500

border-r-indigo-500

border-b-indigo-500

border-l-indigo-500

```
<div class="border-4 border-indigo-200 border-t-indigo-500 ..."></div><div class="border-4 border-indigo-200 border-r-indigo-500 ..."></div><div class="border-4 border-indigo-200 border-b-indigo-500 ..."></div><div class="border-4 border-indigo-200 border-l-indigo-500 ..."></div>
```

### Horizontal and vertical sides

Use utilities likeborder-x-indigo-500andborder-y-lime-100to set the border color on two sides of an element at the same time:

border-x-indigo-500

border-y-indigo-500

```
<div class="border-4 border-indigo-200 border-x-indigo-500 ..."></div><div class="border-4 border-indigo-200 border-y-indigo-500 ..."></div>
```

### Using logical properties

Use utilities likeborder-s-indigo-500andborder-e-lime-100to set theborder-inline-start-colorandborder-inline-end-colorlogical properties, which map to either the left or right border based on the text direction:

Left-to-right

Right-to-left

```
<div dir="ltr">  <div class="border-s-indigo-500 ..."></div></div><div dir="rtl">  <div class="border-s-indigo-500 ..."></div></div>
```

### Divider between children

Use utilities likedivide-indigo-500anddivide-lime-100to control the border color between child elements:

```
<div class="grid grid-cols-3 divide-x-4 divide-indigo-500">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Using a custom value

Use theborder-[<value>]syntaxto set theborder colorbased on a completely custom value:

```
<div class="border-[#243c5a] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theborder-(<custom-property>)syntax:

```
<div class="border-(--my-border) ...">  <!-- ... --></div>
```

This is just a shorthand forborder-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on focus

Prefixaborder-colorutility with a variant likefocus:*to only apply the utility in that state:

```
<input class="border-2 border-gray-700 focus:border-pink-600 ..." />
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixaborder-colorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="border-blue-500 md:border-green-500 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now theborder-regal-blueutility can be used in your markup:

```
<div class="border-regal-blue">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
