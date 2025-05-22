# https://tailwindcss.com/docs/mask-clip

[Original link](https://tailwindcss.com/docs/mask-clip)

## Examples

### Basic example

Use utilities likemask-clip-border,mask-clip-padding, andmask-clip-contentto control the bounding box of an element's mask:

mask-clip-border

mask-clip-padding

mask-clip-content

```
<div class="mask-clip-border border-3 p-1.5 mask-[url(/img/circle.png)] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-clip-padding border-3 p-1.5 mask-[url(/img/circle.png)] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-clip-content border-3 p-1.5 mask-[url(/img/circle.png)] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Responsive design

Prefixamask-cliputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-clip-border md:mask-clip-padding ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
