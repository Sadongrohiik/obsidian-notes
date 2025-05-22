# https://tailwindcss.com/docs/grid-template-columns

[Original link](https://tailwindcss.com/docs/grid-template-columns)

## Examples

### Specifying the grid columns

Usegrid-cols-<number>utilities likegrid-cols-2andgrid-cols-4to create grids withnequally sized columns:

```
<div class="grid grid-cols-4 gap-4">  <div>01</div>  <!-- ... -->  <div>09</div></div>
```

### Implementing a subgrid

Use thegrid-cols-subgridutility to adopt the column tracks defined by the item's parent:

```
<div class="grid grid-cols-4 gap-4">  <div>01</div>  <!-- ... -->  <div>05</div>  <div class="col-span-3 grid grid-cols-subgrid gap-4">    <div class="col-start-2">06</div>  </div></div>
```

### Using a custom value

Use thegrid-cols-[<value>]syntaxto set thecolumnsbased on a completely custom value:

```
<div class="grid-cols-[200px_minmax(900px,_1fr)_100px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thegrid-cols-(<custom-property>)syntax:

```
<div class="grid-cols-(--my-grid-cols) ...">  <!-- ... --></div>
```

This is just a shorthand forgrid-cols-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixagrid-template-columnsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid grid-cols-1 md:grid-cols-6 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
