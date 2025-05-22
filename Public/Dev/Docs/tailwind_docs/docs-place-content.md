# https://tailwindcss.com/docs/place-content

[Original link](https://tailwindcss.com/docs/place-content)

## Examples

### Center

Useplace-content-centerto pack items in the center of the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-center gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Start

Useplace-content-startto pack items against the start of the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-start gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### End

Useplace-content-endto pack items against the end of the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-end gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Space between

Useplace-content-betweento distribute grid items along the block axis so that there is an equal amount of space between each row on the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-between gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Space around

Useplace-content-aroundto distribute grid items such that there is an equal amount of space around each row on the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-around gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Space evenly

Useplace-content-evenlyto distribute grid items such that they are evenly spaced on the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-evenly gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Stretch

Useplace-content-stretchto stretch grid items along their grid areas on the block axis:

```
<div class="grid h-48 grid-cols-2 place-content-stretch gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Responsive design

Prefixaplace-contentutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid place-content-start md:place-content-center ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
