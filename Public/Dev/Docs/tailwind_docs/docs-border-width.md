# https://tailwindcss.com/docs/border-width

[Original link](https://tailwindcss.com/docs/border-width)

## Examples

### Basic example

Useborderorborder-<number>utilities likeborder-2andborder-4to set the border width for all sides of an element:

border

border-2

border-4

border-8

```
<div class="border border-indigo-600 ..."></div><div class="border-2 border-indigo-600 ..."></div><div class="border-4 border-indigo-600 ..."></div><div class="border-8 border-indigo-600 ..."></div>
```

### Individual sides

Use utilities likeborder-randborder-t-4to set the border width for one side of an element:

border-t-4

border-r-4

border-b-4

border-l-4

```
<div class="border-t-4 border-indigo-500 ..."></div><div class="border-r-4 border-indigo-500 ..."></div><div class="border-b-4 border-indigo-500 ..."></div><div class="border-l-4 border-indigo-500 ..."></div>
```

### Horizontal and vertical sides

Use utilities likeborder-xandborder-y-4to set the border width on two sides of an element at the same time:

border-x-4

border-y-4

```
<div class="border-x-4 border-indigo-500 ..."></div><div class="border-y-4 border-indigo-500 ..."></div>
```

### Using logical properties

Use utilities likeborder-sandborder-e-4to set theborder-inline-start-widthandborder-inline-end-widthlogical properties, which map to either the left or right border based on the text direction:

Left-to-right

Right-to-left

```
<div dir="ltr">  <div class="border-s-4 ..."></div></div><div dir="rtl">  <div class="border-s-4 ..."></div></div>
```

### Between children

Use utilities likedivide-xanddivide-y-4to add borders between child elements:

```
<div class="grid grid-cols-3 divide-x-4">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

#### Reversing children order

If your elements are in reverse order (using sayflex-row-reverseorflex-col-reverse), use thedivide-x-reverseordivide-y-reverseutilities to ensure the border is added to the correct side of each element:

```
<div class="flex flex-col-reverse divide-y-4 divide-y-reverse divide-gray-200">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Using a custom value

Use theborder-[<value>]syntaxto set theborder widthbased on a completely custom value:

```
<div class="border-[2vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theborder-(length:<custom-property>)syntax:

```
<div class="border-(length:--my-border-width) ...">  <!-- ... --></div>
```

This is just a shorthand forborder-[length:var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaborder-widthutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="border-2 md:border-t-4 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
