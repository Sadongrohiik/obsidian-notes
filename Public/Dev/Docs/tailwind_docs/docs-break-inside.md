# https://tailwindcss.com/docs/break-inside

[Original link](https://tailwindcss.com/docs/break-inside)

## Examples

### Basic example

Use utilities likebreak-inside-columnandbreak-inside-avoid-pageto control how a column or page break should behave within an element:

```
<div class="columns-2">  <p>Well, let me tell you something, ...</p>  <p class="break-inside-avoid-column">Sure, go ahead, laugh...</p>  <p>Maybe we can live without...</p>  <p>Look. If you think this is...</p></div>
```

### Responsive design

Prefixabreak-insideutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="break-inside-avoid-column md:break-inside-auto ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
