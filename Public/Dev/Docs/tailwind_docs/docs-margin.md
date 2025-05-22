# https://tailwindcss.com/docs/margin

[Original link](https://tailwindcss.com/docs/margin)

## Examples

### Basic example

Usem-<number>utilities likem-4andm-8to control the margin on all sides of an element:

```
<div class="m-8 ...">m-8</div>
```

### Adding margin to a single side

Usemt-<number>,mr-<number>,mb-<number>, andml-<number>utilities likeml-2andmt-6to control the margin on one side of an element:

```
<div class="mt-6 ...">mt-6</div><div class="mr-4 ...">mr-4</div><div class="mb-8 ...">mb-8</div><div class="ml-2 ...">ml-2</div>
```

### Adding horizontal margin

Usemx-<number>utilities likemx-4andmx-8to control the horizontal margin of an element:

```
<div class="mx-8 ...">mx-8</div>
```

### Adding vertical margin

Usemy-<number>utilities likemy-4andmy-8to control the vertical margin of an element:

```
<div class="my-8 ...">my-8</div>
```

### Using negative values

To use a negative margin value, prefix the class name with a dash to convert it to a negative value:

```
<div class="h-16 w-36 bg-sky-400 opacity-20 ..."></div><div class="-mt-8 bg-sky-300 ...">-mt-8</div>
```

### Using logical properties

Usems-<number>orme-<number>utilities likems-4andme-8to set themargin-inline-startandmargin-inline-endlogical properties:

Left-to-right

Right-to-left

```
<div>  <div dir="ltr">    <div class="ms-8 ...">ms-8</div>    <div class="me-8 ...">me-8</div>  </div>  <div dir="rtl">    <div class="ms-8 ...">ms-8</div>    <div class="me-8 ...">me-8</div>  </div></div>
```

### Adding space between children

Usespace-x-<number>orspace-y-<number>utilities likespace-x-4andspace-y-8to control the space between elements:

```
<div class="flex space-x-4 ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

#### Reversing children order

If your elements are in reverse order (using sayflex-row-reverseorflex-col-reverse), use thespace-x-reverseorspace-y-reverseutilities to ensure the space is added to the correct side of each element:

```
<div class="flex flex-row-reverse space-x-4 space-x-reverse ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

#### Limitations

The space utilities are really just a shortcut for adding margin to all-but-the-last-item in a group, and aren't designed to handle complex cases like grids, layouts that wrap, or situations where the children are rendered in a complex custom order rather than their natural DOM order.

For those situations, it's better to use thegap utilitieswhen possible, or add margin to every element with a matching negative margin on the parent.

Additionally, the space utilities are not designed to work together with thedivide utilities. For those situations, consider adding margin/padding utilities to the children instead.

### Using a custom value

Use utilities likem-[<value>],mx-[<value>],andmb-[<value>]to set themarginbased on a completely custom value:

```
<div class="m-[5px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use them-(<custom-property>)syntax:

```
<div class="m-(--my-margin) ...">  <!-- ... --></div>
```

This is just a shorthand form-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamarginutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mt-4 md:mt-8 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Them-<number>,mx-<number>,my-<number>,ms-<number>,me-<number>,mt-<number>,mr-<number>,mb-<number>,andml-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
