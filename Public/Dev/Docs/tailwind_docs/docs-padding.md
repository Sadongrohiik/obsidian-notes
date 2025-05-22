# https://tailwindcss.com/docs/padding

[Original link](https://tailwindcss.com/docs/padding)

## Examples

### Basic example

Usep-<number>utilities likep-4andp-8to control the padding on all sides of an element:

```
<div class="p-8 ...">p-8</div>
```

### Adding padding to one side

Usept-<number>,pr-<number>,pb-<number>, andpl-<number>utilities likept-6andpr-4to control the padding on one side of an element:

```
<div class="pt-6 ...">pt-6</div><div class="pr-4 ...">pr-4</div><div class="pb-8 ...">pb-8</div><div class="pl-2 ...">pl-2</div>
```

### Adding horizontal padding

Usepx-<number>utilities likepx-4andpx-8to control the horizontal padding of an element:

```
<div class="px-8 ...">px-8</div>
```

### Adding vertical padding

Usepy-<number>utilities likepy-4andpy-8to control the vertical padding of an element:

```
<div class="py-8 ...">py-8</div>
```

### Using logical properties

Useps-<number>orpe-<number>utilities likeps-4andpe-8to set thepadding-inline-startandpadding-inline-endlogical properties, which map to either the left or right side based on the text direction:

Left-to-right

Right-to-left

```
<div>  <div dir="ltr">    <div class="ps-8 ...">ps-8</div>    <div class="pe-8 ...">pe-8</div>  </div>  <div dir="rtl">    <div class="ps-8 ...">ps-8</div>    <div class="pe-8 ...">pe-8</div>  </div></div>
```

For more control, you can also use theLTR and RTL modifiersto conditionally apply specific styles depending on the current text direction.

### Using a custom value

Use utilities likep-[<value>],px-[<value>],andpb-[<value>]to set thepaddingbased on a completely custom value:

```
<div class="p-[5px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thep-(<custom-property>)syntax:

```
<div class="p-(--my-padding) ...">  <!-- ... --></div>
```

This is just a shorthand forp-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixapaddingutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="py-4 md:py-8 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Thep-<number>,px-<number>,py-<number>,ps-<number>,pe-<number>,pt-<number>,pr-<number>,pb-<number>,andpl-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
