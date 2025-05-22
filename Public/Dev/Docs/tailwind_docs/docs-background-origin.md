# https://tailwindcss.com/docs/background-origin

[Original link](https://tailwindcss.com/docs/background-origin)

## Examples

### Basic example

Use thebg-origin-border,bg-origin-padding, andbg-origin-contentutilities to control where an element's background is rendered:

bg-origin-border

bg-origin-padding

bg-origin-content

```
<div class="border-4 bg-[url(/img/mountains.jpg)] bg-origin-border p-3 ..."></div><div class="border-4 bg-[url(/img/mountains.jpg)] bg-origin-padding p-3 ..."></div><div class="border-4 bg-[url(/img/mountains.jpg)] bg-origin-content p-3 ..."></div>
```

### Responsive design

Prefixabackground-originutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-origin-border md:bg-origin-padding ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
