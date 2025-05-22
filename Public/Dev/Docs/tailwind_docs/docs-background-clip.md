# https://tailwindcss.com/docs/background-clip

[Original link](https://tailwindcss.com/docs/background-clip)

## Examples

### Basic example

Use thebg-clip-border,bg-clip-padding, andbg-clip-contentutilities to control the bounding box of an element's background:

bg-clip-border

bg-clip-padding

bg-clip-content

```
<div class="border-4 bg-indigo-500 bg-clip-border p-3"></div><div class="border-4 bg-indigo-500 bg-clip-padding p-3"></div><div class="border-4 bg-indigo-500 bg-clip-content p-3"></div>
```

### Cropping to text

Use thebg-clip-textutility to crop an element's background to match the shape of the text:

Hello world

```
<p class="bg-gradient-to-r from-pink-500 to-violet-500 bg-clip-text text-5xl font-extrabold text-transparent ...">  Hello world</p>
```

### Responsive design

Prefixabackground-cliputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-clip-border md:bg-clip-padding ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
