# https://tailwindcss.com/docs/justify-content

[Original link](https://tailwindcss.com/docs/justify-content)

## Examples

### Start

Use thejustify-startutility to justify items against the start of the container's main axis:

```
<div class="flex justify-start ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Center

Use thejustify-centerorjustify-center-safeutilities to justify items along the center of the container's main axis:

Resize the container to see the alignment behavior

justify-center

justify-center-safe

```
<div class="flex justify-center ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

```
<div class="flex justify-center-safe ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

When there is not enough space available, thejustify-center-safeutility will align items to the start of the container instead of the center.

### End

Use thejustify-endorjustify-end-safeutilities to justify items against the end of the container's main axis:

Resize the container to see the alignment behavior

justify-end

justify-end-safe

```
<div class="flex justify-end ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>03</div></div>
```

```
<div class="flex justify-end-safe ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>03</div></div>
```

When there is not enough space available, thejustify-end-safeutility will align items to the start of the container instead of the end.

### Space between

Use thejustify-betweenutility to justify items along the container's main axis such that there is an equal amount of space between each item:

```
<div class="flex justify-between ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Space around

Use thejustify-aroundutility to justify items along the container's main axis such that there is an equal amount of space on each side of each item:

```
<div class="flex justify-around ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Space evenly

Use thejustify-evenlyutility to justify items along the container's main axis such that there is an equal amount of space around each item, but also accounting for the doubling of space you would normally see between each item when usingjustify-around:

```
<div class="flex justify-evenly ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Stretch

Use thejustify-stretchutility to allow content items to fill the available space along the container's main axis:

```
<div class="flex justify-stretch ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Normal

Use thejustify-normalutility to pack content items in their default position as if nojustify-contentvalue was set:

```
<div class="flex justify-normal ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Responsive design

Prefixajustify-contentutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex justify-start md:justify-between ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
