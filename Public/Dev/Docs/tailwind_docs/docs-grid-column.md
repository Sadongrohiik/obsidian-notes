# https://tailwindcss.com/docs/grid-column

[Original link](https://tailwindcss.com/docs/grid-column)

## Examples

### Spanning columns

Usecol-span-<number>utilities likecol-span-2andcol-span-4to make an element spanncolumns:

```
<div class="grid grid-cols-3 gap-4">  <div class="...">01</div>  <div class="...">02</div>  <div class="...">03</div>  <div class="col-span-2 ...">04</div>  <div class="...">05</div>  <div class="...">06</div>  <div class="col-span-2 ...">07</div></div>
```

### Starting and ending lines

Usecol-start-<number>orcol-end-<number>utilities likecol-start-2andcol-end-3to make an element start or end at thenthgrid line:

```
<div class="grid grid-cols-6 gap-4">  <div class="col-span-4 col-start-2 ...">01</div>  <div class="col-start-1 col-end-3 ...">02</div>  <div class="col-span-2 col-end-7 ...">03</div>  <div class="col-start-1 col-end-7 ...">04</div></div>
```

These can also be combined with thecol-span-<number>utilities to span a specific number of columns.

### Using a custom value

Use utilities likecol-[<value>],col-span-[<value>],col-start-[<value>],andcol-end-[<value>]to set thegrid column size and locationbased on a completely custom value:

```
<div class="col-[16_/_span_16] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thecol-(<custom-property>)syntax:

```
<div class="col-(--my-columns) ...">  <!-- ... --></div>
```

This is just a shorthand forcol-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixgrid-column,grid-column-start,andgrid-column-endutilitieswith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="col-span-2 md:col-span-6 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
