# https://tailwindcss.com/docs/background-blend-mode

[Original link](https://tailwindcss.com/docs/background-blend-mode)

## Examples

### Basic example

Use utilities likebg-blend-differenceandbg-blend-saturationto control how the background image and color of an element are blended:

bg-blend-multiply

bg-blend-soft-light

bg-blend-overlay

```
<div class="bg-blue-500 bg-[url(/img/mountains.jpg)] bg-blend-multiply ..."></div><div class="bg-blue-500 bg-[url(/img/mountains.jpg)] bg-blend-soft-light ..."></div><div class="bg-blue-500 bg-[url(/img/mountains.jpg)] bg-blend-overlay ..."></div>
```

### Responsive design

Prefixabackground-blend-modeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-blue-500 bg-[url(/img/mountains.jpg)] bg-blend-lighten md:bg-blend-darken ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
