# https://tailwindcss.com/docs/grid-template-rows

[Original link](https://tailwindcss.com/docs/grid-template-rows)

## Examples

### Specifying the grid rows

Usegrid-rows-<number>utilities likegrid-rows-2andgrid-rows-4to create grids withnequally sized rows:

```
<div class="grid grid-flow-col grid-rows-4 gap-4">  <div>01</div>  <!-- ... -->  <div>09</div></div>
```

### Implementing a subgrid

Use thegrid-rows-subgridutility to adopt the row tracks defined by the item's parent:

```
<div class="grid grid-flow-col grid-rows-4 gap-4">  <div>01</div>  <!-- ... -->  <div>05</div>  <div class="row-span-3 grid grid-rows-subgrid gap-4">    <div class="row-start-2">06</div>  </div>  <div>07</div>  <!-- ... -->  <div>10</div></div>
```

### Using a custom value

Use thegrid-rows-[<value>]syntaxto set therowsbased on a completely custom value:

```
<div class="grid-rows-[200px_minmax(900px,1fr)_100px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thegrid-rows-(<custom-property>)syntax:

```
<div class="grid-rows-(--my-grid-rows) ...">  <!-- ... --></div>
```

This is just a shorthand forgrid-rows-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixagrid-template-rowsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid grid-rows-2 md:grid-rows-6 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
