# https://tailwindcss.com/docs/flex-grow

[Original link](https://tailwindcss.com/docs/flex-grow)

## Examples

### Allowing items to grow

Usegrowto allow a flex item to grow to fill any available space:

```
<div class="flex ...">  <div class="size-14 flex-none ...">01</div>  <div class="size-14 grow ...">02</div>  <div class="size-14 flex-none ...">03</div></div>
```

### Growing items based on factor

Usegrow-<number>utilities likegrow-3to make flex items grow proportionally based on their growth factor, allowing them to fill the available space relative to each other:

```
<div class="flex ...">  <div class="size-14 grow-3 ...">01</div>  <div class="size-14 grow-7 ...">02</div>  <div class="size-14 grow-3 ...">03</div></div>
```

### Preventing items from growing

Usegrow-0to prevent a flex item from growing:

```
<div class="flex ...">  <div class="size-14 grow ...">01</div>  <div class="size-14 grow-0 ...">02</div>  <div class="size-14 grow ...">03</div></div>
```

### Using a custom value

Use thegrow-[<value>]syntaxto set theflex grow factorbased on a completely custom value:

```
<div class="grow-[25vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thegrow-(<custom-property>)syntax:

```
<div class="grow-(--my-grow) ...">  <!-- ... --></div>
```

This is just a shorthand forgrow-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaflex-growutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grow md:grow-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
