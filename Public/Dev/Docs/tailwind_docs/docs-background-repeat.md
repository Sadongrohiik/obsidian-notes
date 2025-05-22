# https://tailwindcss.com/docs/background-repeat

[Original link](https://tailwindcss.com/docs/background-repeat)

## Examples

### Basic example

Use thebg-repeatutility to repeat the background image both vertically and horizontally:

```
<div class="bg-[url(/img/clouds.svg)] bg-center bg-repeat ..."></div>
```

### Repeating horizontally

Use thebg-repeat-xutility to only repeat the background image horizontally:

```
<div class="bg-[url(/img/clouds.svg)] bg-center bg-repeat-x ..."></div>
```

### Repeating vertically

Use thebg-repeat-yutility to only repeat the background image vertically:

```
<div class="bg-[url(/img/clouds.svg)] bg-center bg-repeat-y ..."></div>
```

### Preventing clipping

Use thebg-repeat-spaceutility to repeat the background image without clipping:

```
<div class="bg-[url(/img/clouds.svg)] bg-center bg-repeat-space ..."></div>
```

### Preventing clipping and gaps

Use thebg-repeat-roundutility to repeat the background image without clipping, stretching if needed to avoid gaps:

```
<div class="bg-[url(/img/clouds.svg)] bg-center bg-repeat-round ..."></div>
```

### Disabling repeating

Use thebg-no-repeatutility to prevent a background image from repeating:

```
<div class="bg-[url(/img/clouds.svg)] bg-center bg-no-repeat ..."></div>
```

### Responsive design

Prefixabackground-repeatutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-repeat md:bg-repeat-x ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
