# https://tailwindcss.com/docs/grid-row

[Original link](https://tailwindcss.com/docs/grid-row)

## Examples

### Spanning rows

Userow-span-<number>utilities likerow-span-2androw-span-4to make an element spannrows:

```
<div class="grid grid-flow-col grid-rows-3 gap-4">  <div class="row-span-3 ...">01</div>  <div class="col-span-2 ...">02</div>  <div class="col-span-2 row-span-2 ...">03</div></div>
```

### Starting and ending lines

Userow-start-<number>orrow-end-<number>utilities likerow-start-2androw-end-3to make an element start or end at thenthgrid line:

```
<div class="grid grid-flow-col grid-rows-3 gap-4">  <div class="row-span-2 row-start-2 ...">01</div>  <div class="row-span-2 row-end-3 ...">02</div>  <div class="row-start-1 row-end-4 ...">03</div></div>
```

These can also be combined with therow-span-<number>utilities to span a specific number of rows.

### Using a custom value

Use utilities likerow-[<value>],row-span-[<value>],row-start-[<value>],androw-end-[<value>]to set thegrid row size and locationbased on a completely custom value:

```
<div class="row-[span_16_/_span_16] ...">  <!-- ... --></div>
```

For CSS variables, you can also use therow-(<custom-property>)syntax:

```
<div class="row-(--my-rows) ...">  <!-- ... --></div>
```

This is just a shorthand forrow-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixgrid-row,grid-row-start,andgrid-row-endutilitieswith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="row-span-3 md:row-span-4 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
