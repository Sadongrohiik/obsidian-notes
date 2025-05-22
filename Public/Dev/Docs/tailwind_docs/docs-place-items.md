# https://tailwindcss.com/docs/place-items

[Original link](https://tailwindcss.com/docs/place-items)

## Examples

### Start

Useplace-items-startto place grid items on the start of their grid areas on both axes:

```
<div class="grid grid-cols-3 place-items-start gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### End

Useplace-items-endto place grid items on the end of their grid areas on both axes:

```
<div class="grid h-56 grid-cols-3 place-items-end gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Center

Useplace-items-centerto place grid items on the center of their grid areas on both axes:

```
<div class="grid h-56 grid-cols-3 place-items-center gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Stretch

Useplace-items-stretchto stretch items along their grid areas on both axes:

```
<div class="grid h-56 grid-cols-3 place-items-stretch gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

## Responsive design

Prefixaplace-itemsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid place-items-start md:place-items-center ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
