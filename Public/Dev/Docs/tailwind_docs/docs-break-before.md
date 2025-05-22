# https://tailwindcss.com/docs/break-before

[Original link](https://tailwindcss.com/docs/break-before)

## Examples

### Basic example

Use utilities likebreak-before-columnandbreak-before-pageto control how a column or page break should behave before an element:

```
<div class="columns-2">  <p>Well, let me tell you something, ...</p>  <p class="break-before-column">Sure, go ahead, laugh...</p>  <p>Maybe we can live without...</p>  <p>Look. If you think this is...</p></div>
```

### Responsive design

Prefixabreak-beforeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="break-before-column md:break-before-auto ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
