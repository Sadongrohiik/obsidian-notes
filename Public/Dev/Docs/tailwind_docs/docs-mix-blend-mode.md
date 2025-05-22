# https://tailwindcss.com/docs/mix-blend-mode

[Original link](https://tailwindcss.com/docs/mix-blend-mode)

## Examples

### Basic example

Use utilities likemix-blend-overlayandmix-blend-soft-lightto control how an element's content and background is blended with other content in the same stacking context:

```
<div class="flex justify-center -space-x-14">  <div class="bg-blue-500 mix-blend-multiply ..."></div>  <div class="bg-pink-500 mix-blend-multiply ..."></div></div>
```

### Isolating blending

Use theisolateutility on the parent element to create a new stacking context and prevent blending with content behind it:

```
<div class="isolate flex justify-center -space-x-14">  <div class="bg-yellow-500 mix-blend-multiply ..."></div>  <div class="bg-green-500 mix-blend-multiply ..."></div></div><div class="flex justify-center -space-x-14">  <div class="bg-yellow-500 mix-blend-multiply ..."></div>  <div class="bg-green-500 mix-blend-multiply ..."></div></div>
```

### Responsive design

Prefixamix-blend-modeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mix-blend-multiply md:mix-blend-overlay ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
