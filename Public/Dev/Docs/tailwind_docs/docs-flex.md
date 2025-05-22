# https://tailwindcss.com/docs/flex

[Original link](https://tailwindcss.com/docs/flex)

## Examples

### Basic example

Useflex-<number>utilities likeflex-1to allow a flex item to grow and shrink as needed, ignoring its initial size:

```
<div class="flex">  <div class="w-14 flex-none ...">01</div>  <div class="w-64 flex-1 ...">02</div>  <div class="w-32 flex-1 ...">03</div></div>
```

### Initial

Useflex-initialto allow a flex item to shrink but not grow, taking into account its initial size:

```
<div class="flex">  <div class="w-14 flex-none ...">01</div>  <div class="w-64 flex-initial ...">02</div>  <div class="w-32 flex-initial ...">03</div></div>
```

### Auto

Useflex-autoto allow a flex item to grow and shrink, taking into account its initial size:

```
<div class="flex ...">  <div class="w-14 flex-none ...">01</div>  <div class="w-64 flex-auto ...">02</div>  <div class="w-32 flex-auto ...">03</div></div>
```

### None

Useflex-noneto prevent a flex item from growing or shrinking:

```
<div class="flex ...">  <div class="w-14 flex-none ...">01</div>  <div class="w-32 flex-none ...">02</div>  <div class="flex-1 ...">03</div></div>
```

### Using a custom value

Use theflex-[<value>]syntaxto set theflex shorthand propertybased on a completely custom value:

```
<div class="flex-[3_1_auto] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theflex-(<custom-property>)syntax:

```
<div class="flex-(--my-flex) ...">  <!-- ... --></div>
```

This is just a shorthand forflex-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaflexutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex-none md:flex-1 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
