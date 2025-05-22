# https://tailwindcss.com/docs/flex-shrink

[Original link](https://tailwindcss.com/docs/flex-shrink)

## Examples

### Allowing flex items to shrink

Useshrinkto allow a flex item to shrink if needed:

```
<div class="flex ...">  <div class="h-14 w-14 flex-none ...">01</div>  <div class="h-14 w-64 shrink ...">02</div>  <div class="h-14 w-14 flex-none ...">03</div></div>
```

### Preventing items from shrinking

Useshrink-0to prevent a flex item from shrinking:

```
<div class="flex ...">  <div class="h-16 flex-1 ...">01</div>  <div class="h-16 w-32 shrink-0 ...">02</div>  <div class="h-16 flex-1 ...">03</div></div>
```

### Using a custom value

Use theshrink-[<value>]syntaxto set theflex shrink factorbased on a completely custom value:

```
<div class="shrink-[calc(100vw-var(--sidebar))] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theshrink-(<custom-property>)syntax:

```
<div class="shrink-(--my-shrink) ...">  <!-- ... --></div>
```

This is just a shorthand forshrink-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaflex-shrinkutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="shrink md:shrink-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
