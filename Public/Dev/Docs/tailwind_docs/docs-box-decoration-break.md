# https://tailwindcss.com/docs/box-decoration-break

[Original link](https://tailwindcss.com/docs/box-decoration-break)

## Examples

### Basic example

Use thebox-decoration-sliceandbox-decoration-cloneutilities to control whether properties like background, border, border-image, box-shadow, clip-path, margin, and padding should be rendered as if the element were one continuous fragment, or distinct blocks:

box-decoration-slice

box-decoration-clone

```
<span class="box-decoration-slice bg-linear-to-r from-indigo-600 to-pink-500 px-2 text-white ...">  Hello<br />World</span><span class="box-decoration-clone bg-linear-to-r from-indigo-600 to-pink-500 px-2 text-white ...">  Hello<br />World</span>
```

### Responsive design

Prefixabox-decoration-breakutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="box-decoration-clone md:box-decoration-slice ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
