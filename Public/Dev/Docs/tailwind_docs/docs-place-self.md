# https://tailwindcss.com/docs/place-self

[Original link](https://tailwindcss.com/docs/place-self)

## Examples

### Auto

Useplace-self-autoto align an item based on the value of the container'splace-itemsproperty:

```
<div class="grid grid-cols-3 gap-4 ...">  <div>01</div>  <div class="place-self-auto ...">02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Start

Useplace-self-startto align an item to the start on both axes:

```
<div class="grid grid-cols-3 gap-4 ...">  <div>01</div>  <div class="place-self-start ...">02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Center

Useplace-self-centerto align an item at the center on both axes:

```
<div class="grid grid-cols-3 gap-4 ...">  <div>01</div>  <div class="place-self-center ...">02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### End

Useplace-self-endto align an item to the end on both axes:

```
<div class="grid grid-cols-3 gap-4 ...">  <div>01</div>  <div class="place-self-end ...">02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Stretch

Useplace-self-stretchto stretch an item on both axes:

```
<div class="grid grid-cols-3 gap-4 ...">  <div>01</div>  <div class="place-self-stretch ...">02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Responsive design

Prefixaplace-selfutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="place-self-start md:place-self-end ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
