# https://tailwindcss.com/docs/flex-direction

[Original link](https://tailwindcss.com/docs/flex-direction)

## Examples

### Row

Useflex-rowto position flex items horizontally in the same direction as text:

```
<div class="flex flex-row ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Row reversed

Useflex-row-reverseto position flex items horizontally in the opposite direction:

```
<div class="flex flex-row-reverse ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Column

Useflex-colto position flex items vertically:

```
<div class="flex flex-col ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Column reversed

Useflex-col-reverseto position flex items vertically in the opposite direction:

```
<div class="flex flex-col-reverse ...">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Responsive design

Prefixaflex-directionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex flex-col md:flex-row ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
