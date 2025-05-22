# https://tailwindcss.com/docs/scroll-padding

[Original link](https://tailwindcss.com/docs/scroll-padding)

## Examples

### Basic example

Use thescroll-pt-<number>,scroll-pr-<number>,scroll-pb-<number>, andscroll-pl-<number>utilities likescroll-pl-4andscroll-pt-6to set the scroll offset of an element within a snap container:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x scroll-pl-6 ...">  <div class="snap-start ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-05.jpg" />  </div></div>
```

### Using logical properties

Use thescroll-ps-<number>andscroll-pe-<number>utilities to set thescroll-padding-inline-startandscroll-padding-inline-endlogical properties, which map to either the left or right side based on the text direction:

Scroll in the grid of images to see the expected behavior

Left-to-right

Right-to-left

```
<div dir="ltr">  <div class="snap-x scroll-ps-6 ...">    <!-- ... -->  </div></div><div dir="rtl">  <div class="snap-x scroll-ps-6 ...">    <!-- ... -->  </div></div>
```

### Using negative values

To use a negative scroll padding value, prefix the class name with a dash to convert it to a negative value:

```
<div class="-scroll-ps-6 snap-x ...">  <!-- ... --></div>
```

### Using a custom value

Use utilities likescroll-pl-[<value>]andscroll-pe-[<value>]to set thescroll paddingbased on a completely custom value:

```
<div class="scroll-pl-[24rem] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thescroll-pl-(<custom-property>)syntax:

```
<div class="scroll-pl-(--my-scroll-padding) ...">  <!-- ... --></div>
```

This is just a shorthand forscroll-pl-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixascroll-paddingutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="scroll-p-8 md:scroll-p-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Thescroll-p-<number>,scroll-px-<number>,scroll-py-<number>,scroll-ps-<number>,scroll-pe-<number>,scroll-pt-<number>,scroll-pr-<number>,scroll-pb-<number>,andscroll-pl-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
