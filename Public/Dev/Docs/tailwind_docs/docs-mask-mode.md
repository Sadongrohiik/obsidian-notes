# https://tailwindcss.com/docs/mask-mode

[Original link](https://tailwindcss.com/docs/mask-mode)

## Examples

### Basic example

Use themask-alpha,mask-luminanceandmask-matchutilities to control the mode of an element's mask:

mask-alpha

mask-luminance

```
<div class="mask-alpha mask-r-from-black mask-r-from-50% mask-r-to-transparent bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-luminance mask-r-from-white mask-r-from-50% mask-r-to-black bg-[url(/img/mountains.jpg)] ..."></div>
```

When usingmask-luminancethe luminance value of the mask determines visibility, so sticking with grayscale colors will produce the most predictable results. Withmask-alpha, the opacity of the mask determines the visibility of the masked element.

### Responsive design

Prefixamask-modeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-alpha md:mask-luminance ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
