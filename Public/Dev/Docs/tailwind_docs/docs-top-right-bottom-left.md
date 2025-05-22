# https://tailwindcss.com/docs/top-right-bottom-left

[Original link](https://tailwindcss.com/docs/top-right-bottom-left)

## Examples

### Basic example

Usetop-<number>,right-<number>,bottom-<number>,left-<number>, andinset-<number>utilities liketop-0andbottom-4to set the horizontal or vertical position of apositioned element:

```
<!-- Pin to top left corner --><div class="relative size-32 ...">  <div class="absolute top-0 left-0 size-16 ...">01</div></div><!-- Span top edge --><div class="relative size-32 ...">  <div class="absolute inset-x-0 top-0 h-16 ...">02</div></div><!-- Pin to top right corner --><div class="relative size-32 ...">  <div class="absolute top-0 right-0 size-16 ...">03</div></div><!-- Span left edge --><div class="relative size-32 ...">  <div class="absolute inset-y-0 left-0 w-16 ...">04</div></div><!-- Fill entire parent --><div class="relative size-32 ...">  <div class="absolute inset-0 ...">05</div></div><!-- Span right edge --><div class="relative size-32 ...">  <div class="absolute inset-y-0 right-0 w-16 ...">06</div></div><!-- Pin to bottom left corner --><div class="relative size-32 ...">  <div class="absolute bottom-0 left-0 size-16 ...">07</div></div><!-- Span bottom edge --><div class="relative size-32 ...">  <div class="absolute inset-x-0 bottom-0 h-16 ...">08</div></div><!-- Pin to bottom right corner --><div class="relative size-32 ...">  <div class="absolute right-0 bottom-0 size-16 ...">09</div></div>
```

### Using negative values

To use a negative top/right/bottom/left value, prefix the class name with a dash to convert it to a negative value:

```
<div class="relative size-32 ...">  <div class="absolute -top-4 -left-4 size-14 ..."></div></div>
```

### Using logical properties

Usestart-<number>orend-<number>utilities likestart-0andend-4to set theinset-inline-startandinset-inline-endlogical properties, which map to either the left or right side based on the text direction:

Left-to-right

Right-to-left

```
<div dir="ltr">  <div class="relative size-32 ...">    <div class="absolute start-0 top-0 size-14 ..."></div>  </div>  <div>    <div dir="rtl">      <div class="relative size-32 ...">        <div class="absolute start-0 top-0 size-14 ..."></div>      </div>      <div></div>    </div>  </div></div>
```

For more control, you can also use theLTR and RTL modifiersto conditionally apply specific styles depending on the current text direction.

### Using a custom value

Use utilities likeinset-[<value>]andtop-[<value>]to set thepositionbased on a completely custom value:

```
<div class="inset-[3px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theinset-(<custom-property>)syntax:

```
<div class="inset-(--my-position) ...">  <!-- ... --></div>
```

This is just a shorthand forinset-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixinset,inset-x,inset-y,start,end,top,left,bottom,andrightutilitieswith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="top-4 md:top-6 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Theinset-<number>,inset-x-<number>,inset-y-<number>,start-<number>,end-<number>,top-<number>,left-<number>,bottom-<number>,andright-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
