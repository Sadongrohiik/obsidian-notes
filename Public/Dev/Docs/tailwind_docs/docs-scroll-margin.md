# https://tailwindcss.com/docs/scroll-margin

[Original link](https://tailwindcss.com/docs/scroll-margin)

## Examples

### Basic example

Use thescroll-mt-<number>,scroll-mr-<number>,scroll-mb-<number>, andscroll-ml-<number>utilities likescroll-ml-4andscroll-mt-6to set the scroll offset around items within a snap container:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x ...">  <div class="snap-start scroll-ml-6 ...">    <img src="/img/vacation-01.jpg"/>  </div>  <div class="snap-start scroll-ml-6 ...">    <img src="/img/vacation-02.jpg"/>  </div>  <div class="snap-start scroll-ml-6 ...">    <img src="/img/vacation-03.jpg"/>  </div>  <div class="snap-start scroll-ml-6 ...">    <img src="/img/vacation-04.jpg"/>  </div>  <div class="snap-start scroll-ml-6 ...">    <img src="/img/vacation-05.jpg"/>  </div></div>
```

### Using negative values

To use a negative scroll margin value, prefix the class name with a dash to convert it to a negative value:

```
<div class="snap-start -scroll-ml-6 ...">  <!-- ... --></div>
```

### Using logical properties

Use thescroll-ms-<number>andscroll-me-<number>utilities to set thescroll-margin-inline-startandscroll-margin-inline-endlogical properties, which map to either the left or right side based on the text direction:

Scroll in the grid of images to see the expected behavior

Left-to-right

Right-to-left

```
<div dir="ltr">  <div class="snap-x ...">    <div class="snap-start scroll-ms-6 ...">      <img src="/img/vacation-01.jpg"/>    </div>    <!-- ... -->  </div></div><div dir="rtl">  <div class="snap-x ...">    <div class="snap-start scroll-ms-6 ...">      <img src="/img/vacation-01.jpg"/>    </div>    <!-- ... -->  </div></div>
```

For more control, you can also use theLTR and RTL modifiersto conditionally apply specific styles depending on the current text direction.

### Using a custom value

Use utilities likescroll-ml-[<value>]andscroll-me-[<value>]to set thescroll marginbased on a completely custom value:

```
<div class="scroll-ml-[24rem] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thescroll-ml-(<custom-property>)syntax:

```
<div class="scroll-ml-(--my-scroll-margin) ...">  <!-- ... --></div>
```

This is just a shorthand forscroll-ml-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixascroll-marginutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="scroll-m-8 md:scroll-m-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Thescroll-m-<number>,scroll-mx-<number>,scroll-my-<number>,scroll-ms-<number>,scroll-me-<number>,scroll-mt-<number>,scroll-mr-<number>,scroll-mb-<number>,andscroll-ml-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
