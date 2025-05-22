# https://tailwindcss.com/docs/mask-position

[Original link](https://tailwindcss.com/docs/mask-position)

## Examples

### Basic example

Use utilities likemask-center,mask-right, andmask-left-topto control the position of an element's mask image:

mask-top-left

mask-top

mask-top-right

mask-left

mask-center

mask-right

mask-bottom-left

mask-bottom

mask-bottom-right

```
<div class="mask-top-left mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-top mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-top-right mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-left mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-center mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-right mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-bottom-left mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-bottom mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-bottom-right mask-[url(/img/circle.png)] mask-size-[50%] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Using a custom value

Use themask-position-[<value>]syntaxto set themask positionbased on a completely custom value:

```
<div class="mask-position-[center_top_1rem] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themask-position-(<custom-property>)syntax:

```
<div class="mask-position-(--my-mask-position) ...">  <!-- ... --></div>
```

This is just a shorthand formask-position-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamask-positionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-center md:mask-top ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
