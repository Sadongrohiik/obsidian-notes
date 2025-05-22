# https://tailwindcss.com/docs/border-style

[Original link](https://tailwindcss.com/docs/border-style)

## Examples

### Basic example

Use utilities likeborder-solidandborder-dottedto control an element's border style:

border-solid

border-dashed

border-dotted

border-double

```
<div class="border-2 border-solid ..."></div><div class="border-2 border-dashed ..."></div><div class="border-2 border-dotted ..."></div><div class="border-4 border-double ..."></div>
```

### Removing a border

Use theborder-noneutility to remove an existing border from an element:

```
<button class="border-none ...">Save Changes</button>
```

This is most commonly used to remove a border style that was applied at a smaller breakpoint.

### Setting the divider style

Use utilities likedivide-dashedanddivide-dottedto control the border style between child elements:

```
<div class="grid grid-cols-3 divide-x-3 divide-dashed divide-indigo-500">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Responsive design

Prefixaborder-styleutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="border-solid md:border-dotted ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
