# https://tailwindcss.com/docs/flex-wrap

[Original link](https://tailwindcss.com/docs/flex-wrap)

## Examples

### Don't wrap

Useflex-nowrapto prevent flex items from wrapping, causing inflexible items to overflow the container if necessary:

```
<div class="flex flex-nowrap">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Wrap normally

Useflex-wrapto allow flex items to wrap:

```
<div class="flex flex-wrap">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Wrap reversed

Useflex-wrap-reverseto wrap flex items in the reverse direction:

```
<div class="flex flex-wrap-reverse">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Responsive design

Prefixaflex-wraputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex flex-wrap md:flex-wrap-reverse ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
