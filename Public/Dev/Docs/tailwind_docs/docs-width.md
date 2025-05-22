# https://tailwindcss.com/docs/width

[Original link](https://tailwindcss.com/docs/width)

## Examples

### Basic example

Usew-<number>utilities likew-24andw-64to set an element to a fixed width based on the spacing scale:

```
<div class="w-96 ...">w-96</div><div class="w-80 ...">w-80</div><div class="w-64 ...">w-64</div><div class="w-48 ...">w-48</div><div class="w-40 ...">w-40</div><div class="w-32 ...">w-32</div><div class="w-24 ...">w-24</div>
```

### Using a percentage

Usew-fullorw-<fraction>utilities likew-1/2andw-2/5to give an element a percentage-based width:

```
<div class="flex ...">  <div class="w-1/2 ...">w-1/2</div>  <div class="w-1/2 ...">w-1/2</div></div><div class="flex ...">  <div class="w-2/5 ...">w-2/5</div>  <div class="w-3/5 ...">w-3/5</div></div><div class="flex ...">  <div class="w-1/3 ...">w-1/3</div>  <div class="w-2/3 ...">w-2/3</div></div><div class="flex ...">  <div class="w-1/4 ...">w-1/4</div>  <div class="w-3/4 ...">w-3/4</div></div><div class="flex ...">  <div class="w-1/5 ...">w-1/5</div>  <div class="w-4/5 ...">w-4/5</div></div><div class="flex ...">  <div class="w-1/6 ...">w-1/6</div>  <div class="w-5/6 ...">w-5/6</div></div><div class="w-full ...">w-full</div>
```

### Using the container scale

Use utilities likew-smandw-xlto set an element to a fixed width based on the container scale:

```
<div class="w-xl ...">w-xl</div><div class="w-lg ...">w-lg</div><div class="w-md ...">w-md</div><div class="w-sm ...">w-sm</div><div class="w-xs ...">w-xs</div><div class="w-2xs ...">w-2xs</div><div class="w-3xs ...">w-3xs</div>
```

### Matching the viewport

Use thew-screenutility to make an element span the entire width of the viewport:

```
<div class="w-screen">  <!-- ... --></div>
```

Alternatively, you can match the width of the large, small or dynamic viewports using thew-lvw,w-svw, andw-dvwutilities.

### Resetting the width

Use thew-autoutility to remove an element's assigned width under a specific condition, like at a particular breakpoint:

```
<div class="w-full md:w-auto">  <!-- ... --></div>
```

### Setting both width and height

Use utilities likesize-px,size-4, andsize-fullto set both the width and height of an element at the same time:

```
<div class="size-16 ...">size-16</div><div class="size-20 ...">size-20</div><div class="size-24 ...">size-24</div><div class="size-32 ...">size-32</div><div class="size-40 ...">size-40</div>
```

### Using a custom value

Use thew-[<value>]syntaxto set thewidthbased on a completely custom value:

```
<div class="w-[5px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thew-(<custom-property>)syntax:

```
<div class="w-(--my-width) ...">  <!-- ... --></div>
```

This is just a shorthand forw-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixawidthutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="w-1/2 md:w-full ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Thew-<number>andsize-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
