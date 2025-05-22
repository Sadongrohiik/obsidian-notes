# https://tailwindcss.com/docs/mask-repeat

[Original link](https://tailwindcss.com/docs/mask-repeat)

## Examples

### Basic example

Use themask-repeatutility to repeat the mask image both vertically and horizontally:

```
<div class="mask-repeat mask-[url(/img/circle.png)] mask-size-[50px_50px] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Repeating horizontally

Use themask-repeat-xutility to only repeat the mask image horizontally:

```
<div class="mask-repeat-x mask-[url(/img/circle.png)] mask-size-[50px_50px] bg-[url(/img/mountains.jpg)]..."></div>
```

### Repeating vertically

Use themask-repeat-yutility to only repeat the mask image vertically:

```
<div class="mask-repeat-y mask-[url(/img/circle.png)] mask-size-[50px_50px] bg-[url(/img/mountains.jpg)]..."></div>
```

### Preventing clipping

Use themask-repeat-spaceutility to repeat the mask image without clipping:

```
<div class="mask-repeat-space mask-[url(/img/circle.png)] mask-size-[50px_50px] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Preventing clipping and gaps

Use themask-repeat-roundutility to repeat the mask image without clipping, stretching if needed to avoid gaps:

```
<div class="mask-repeat-round mask-[url(/img/circle.png)] mask-size-[50px_50px] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Disabling repeating

Use themask-no-repeatutility to prevent a mask image from repeating:

```
<div class="mask-no-repeat mask-[url(/img/circle.png)] mask-size-[50px_50px] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Responsive design

Prefixamask-repeatutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-repeat md:mask-repeat-x ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
