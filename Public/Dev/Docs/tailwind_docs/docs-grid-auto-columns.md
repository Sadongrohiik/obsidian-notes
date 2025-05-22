# https://tailwindcss.com/docs/grid-auto-columns

[Original link](https://tailwindcss.com/docs/grid-auto-columns)

## Examples

### Basic example

Use utilities likeauto-cols-minandauto-cols-maxto control the size of implicitly-created grid columns:

```
<div class="grid auto-cols-max grid-flow-col">  <div>01</div>  <div>02</div>  <div>03</div></div>
```

### Using a custom value

Use theauto-cols-[<value>]syntaxto set thesize of implicitly-created grid columnsbased on a completely custom value:

```
<div class="auto-cols-[minmax(0,2fr)] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theauto-cols-(<custom-property>)syntax:

```
<div class="auto-cols-(--my-auto-cols) ...">  <!-- ... --></div>
```

This is just a shorthand forauto-cols-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixagrid-auto-columnsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid grid-flow-col auto-cols-max md:auto-cols-min ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
