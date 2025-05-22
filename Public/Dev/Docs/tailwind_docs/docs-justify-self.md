# https://tailwindcss.com/docs/justify-self

[Original link](https://tailwindcss.com/docs/justify-self)

## Examples

### Auto

Use thejustify-self-autoutility to align an item based on the value of the grid'sjustify-itemsproperty:

```
<div class="grid justify-items-stretch ...">  <!-- ... -->  <div class="justify-self-auto ...">02</div>  <!-- ... --></div>
```

### Start

Use thejustify-self-startutility to align a grid item to the start of its inline axis:

```
<div class="grid justify-items-stretch ...">  <!-- ... -->  <div class="justify-self-start ...">02</div>  <!-- ... --></div>
```

### Center

Use thejustify-self-centerorjustify-self-center-safeutilities to align a grid item along the center of its inline axis:

Resize the container to see the alignment behavior

justify-self-center

justify-self-center-safe

```
<div class="grid justify-items-stretch ...">  <!-- ... -->  <div class="justify-self-center ...">02</div>  <!-- ... --></div>
```

```
<div class="grid justify-items-stretch ...">  <!-- ... -->  <div class="justify-self-center-safe ...">02</div>  <!-- ... --></div>
```

When there is not enough space available, thejustify-self-center-safeutility will align the item to the start of the container instead of the end.

### End

Use thejustify-self-endorjustify-self-end-safeutilities to align a grid item to the end of its inline axis:

Resize the container to see the alignment behavior

justify-self-end

justify-self-end-safe

```
<div class="grid justify-items-stretch ...">  <!-- ... -->  <div class="justify-self-end ...">02</div>  <!-- ... --></div>
```

```
<div class="grid justify-items-stretch ...">  <!-- ... -->  <div class="justify-self-end-safe ...">02</div>  <!-- ... --></div>
```

When there is not enough space available, thejustify-self-end-safeutility will align the item to the start of the container instead of the end.

### Stretch

Use thejustify-self-stretchutility to stretch a grid item to fill the grid area on its inline axis:

```
<div class="grid justify-items-start ...">  <!-- ... -->  <div class="justify-self-stretch ...">02</div>  <!-- ... --></div>
```

### Responsive design

Prefixajustify-selfutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="justify-self-start md:justify-self-end ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
