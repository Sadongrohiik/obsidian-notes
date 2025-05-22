# https://tailwindcss.com/docs/background-position

[Original link](https://tailwindcss.com/docs/background-position)

## Examples

### Basic example

Use utilities likebg-center,bg-right, andbg-top-leftto control the position of an element's background image:

Hover over these examples to see the full image

bg-top-left

bg-top

bg-top-right

bg-left

bg-center

bg-right

bg-bottom-left

bg-bottom

bg-bottom-right

```
<div class="bg-[url(/img/mountains.jpg)] bg-top-left"></div><div class="bg-[url(/img/mountains.jpg)] bg-top"></div><div class="bg-[url(/img/mountains.jpg)] bg-top-right"></div><div class="bg-[url(/img/mountains.jpg)] bg-left"></div><div class="bg-[url(/img/mountains.jpg)] bg-center"></div><div class="bg-[url(/img/mountains.jpg)] bg-right"></div><div class="bg-[url(/img/mountains.jpg)] bg-bottom-left"></div><div class="bg-[url(/img/mountains.jpg)] bg-bottom"></div><div class="bg-[url(/img/mountains.jpg)] bg-bottom-right"></div>
```

### Using a custom value

Use thebg-position-[<value>]syntaxto set thebackground positionbased on a completely custom value:

```
<div class="bg-position-[center_top_1rem] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebg-position-(<custom-property>)syntax:

```
<div class="bg-position-(--my-bg-position) ...">  <!-- ... --></div>
```

This is just a shorthand forbg-position-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackground-positionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-center md:bg-top ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
