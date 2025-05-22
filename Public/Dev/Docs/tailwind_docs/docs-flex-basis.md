# https://tailwindcss.com/docs/flex-basis

[Original link](https://tailwindcss.com/docs/flex-basis)

## Examples

### Using the spacing scale

Usebasis-<number>utilities likebasis-64andbasis-128to set the initial size of flex items based on the spacing scale:

```
<div class="flex flex-row">  <div class="basis-64">01</div>  <div class="basis-64">02</div>  <div class="basis-128">03</div></div>
```

### Using the container scale

Use utilities likebasis-xsandbasis-smto set the initial size of flex items based on the container scale:

```
<div class="flex flex-row">  <div class="basis-3xs">01</div>  <div class="basis-2xs">02</div>  <div class="basis-xs">03</div>  <div class="basis-sm">04</div></div>
```

### Using percentages

Usebasis-<fraction>utilities likebasis-1/2andbasis-2/3to set the initial size of flex items:

```
<div class="flex flex-row">  <div class="basis-1/3">01</div>  <div class="basis-2/3">02</div></div>
```

### Using a custom value

Use thebasis-[<value>]syntaxto set thebasisbased on a completely custom value:

```
<div class="basis-[30vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebasis-(<custom-property>)syntax:

```
<div class="basis-(--my-basis) ...">  <!-- ... --></div>
```

This is just a shorthand forbasis-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaflex-basisutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex flex-row">  <div class="basis-1/4 md:basis-1/3">01</div>  <div class="basis-1/4 md:basis-1/3">02</div>  <div class="basis-1/2 md:basis-1/3">03</div></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--container-*theme variables to customize thefixed-width basisutilities in your project:

```
@theme {  --container-4xs: 14rem; }
```

Now thebasis-4xsutility can be used in your markup:

```
<div class="basis-4xs">  <!-- ... --></div>
```

Thebasis-<number>utilities are driven by the--spacingtheme variable, which you can also customize:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme documentation.
