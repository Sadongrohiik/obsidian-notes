# https://tailwindcss.com/docs/mask-origin

[Original link](https://tailwindcss.com/docs/mask-origin)

## Examples

### Basic example

Use utilities likemask-origin-border,mask-origin-padding, andmask-origin-contentto control where an element's mask is rendered:

mask-origin-border

mask-origin-padding

mask-origin-content

```
<div class="mask-origin-border border-3 p-1.5 mask-[url(/img/circle.png)] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-origin-padding border-3 p-1.5 mask-[url(/img/circle.png)] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-origin-content border-3 p-1.5 mask-[url(/img/circle.png)] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Responsive design

Prefixamask-originutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-origin-border md:mask-origin-padding ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
