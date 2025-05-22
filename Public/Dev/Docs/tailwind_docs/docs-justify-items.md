# https://tailwindcss.com/docs/justify-items

[Original link](https://tailwindcss.com/docs/justify-items)

## Examples

### Start

Use thejustify-items-startutility to justify grid items against the start of their inline axis:

```
<div class="grid justify-items-start ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### End

Use thejustify-items-endorjustify-items-end-safeutilities to justify grid items against the end of their inline axis:

Resize the container to see the alignment behavior

justify-items-end

justify-items-end-safe

```
<div class="grid grid-flow-col justify-items-end ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

```
<div class="grid grid-flow-col justify-items-end-safe ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

When there is not enough space available, thejustify-items-end-safeutility will align items to the start of the container instead of the end.

### Center

Use thejustify-items-centerorjustify-items-center-safeutilities to justify grid items against the end of their inline axis:

Resize the container to see the alignment behavior

justify-items-center

justify-items-center-safe

```
<div class="grid grid-flow-col justify-items-center ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

```
<div class="grid grid-flow-col justify-items-center-safe ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

When there is not enough space available, thejustify-items-center-safeutility will align items to the start of the container instead of the center.

### Stretch

Use thejustify-items-stretchutility to stretch items along their inline axis:

```
<div class="grid justify-items-stretch ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Responsive design

Prefixajustify-itemsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid justify-items-start md:justify-items-center ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
