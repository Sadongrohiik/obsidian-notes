# https://tailwindcss.com/docs/grid-auto-rows

[Original link](https://tailwindcss.com/docs/grid-auto-rows)

## Examples

### Basic example

Use utilities likeauto-rows-minandauto-rows-maxto control the size of implicitly-created grid rows:

```
<div class="grid grid-flow-row auto-rows-max">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Using a custom value

Use theauto-rows-[<value>]syntaxto set thesize of implicitly-created grid rowsbased on a completely custom value:

```
<div class="auto-rows-[minmax(0,2fr)] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theauto-rows-(<custom-property>)syntax:

```
<div class="auto-rows-(--my-auto-rows) ...">  <!-- ... --></div>
```

This is just a shorthand forauto-rows-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixagrid-auto-rowsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid grid-flow-row auto-rows-max md:auto-rows-min ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
