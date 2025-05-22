# https://tailwindcss.com/docs/mask-type

[Original link](https://tailwindcss.com/docs/mask-type)

## Examples

### Basic example

Use themask-type-alphaandmask-type-luminanceutilities to control the type of an SVG mask:

mask-type-alpha

mask-type-luminance

```
<svg>  <mask id="blob1" class="mask-type-alpha fill-gray-700/70">    <path d="..."></path>  </mask>  <image href="/img/mountains.jpg" height="100%" width="100%" mask="url(#blob1)" /></svg><svg>  <mask id="blob2" class="mask-type-luminance fill-gray-700/70">    <path d="..."></path>  </mask>  <image href="/img/mountains.jpg" height="100%" width="100%" mask="url(#blob2)" /></svg>
```

When usingmask-type-luminancethe luminance value of the SVG mask determines visibility, so sticking with grayscale colors will produce the most predictable results. Withmask-alpha, the opacity of the SVG mask determines the visibility of the masked element.

### Responsive design

Prefixamask-typeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<mask class="mask-type-alpha md:mask-type-luminance ...">  <!-- ... --></mask>
```

Learn more about using variants in thevariants documentation.
