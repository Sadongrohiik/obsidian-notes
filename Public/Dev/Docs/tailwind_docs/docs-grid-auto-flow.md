# https://tailwindcss.com/docs/grid-auto-flow

[Original link](https://tailwindcss.com/docs/grid-auto-flow)

## Examples

### Basic example

Use utilities likegrid-flow-colandgrid-flow-row-denseto control how the auto-placement algorithm works for a grid layout:

```
<div class="grid grid-flow-row-dense grid-cols-3 grid-rows-3 ...">  <div class="col-span-2">01</div>  <div class="col-span-2">02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Responsive design

Prefixagrid-auto-flowutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid grid-flow-col md:grid-flow-row ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
