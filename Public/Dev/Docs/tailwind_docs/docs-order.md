# https://tailwindcss.com/docs/order

[Original link](https://tailwindcss.com/docs/order)

## Examples

### Explicitly setting a sort order

Useorder-<number>utilities likeorder-1andorder-3to render flex and grid items in a different order than they appear in the document:

```
<div class="flex justify-between ...">  <div class="order-3 ...">01</div>  <div class="order-1 ...">02</div>  <div class="order-2 ...">03</div></div>
```

### Ordering items first or last

Use theorder-firstandorder-lastutilities to render flex and grid items first or last:

```
<div class="flex justify-between ...">  <div class="order-last ...">01</div>  <div class="...">02</div>  <div class="order-first ...">03</div></div>
```

### Using negative values

To use a negative order value, prefix the class name with a dash to convert it to a negative value:

```
<div class="-order-1">  <!-- ... --></div>
```

### Using a custom value

Use theorder-[<value>]syntaxto set theorderbased on a completely custom value:

```
<div class="order-[min(var(--total-items),10)] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theorder-(<custom-property>)syntax:

```
<div class="order-(--my-order) ...">  <!-- ... --></div>
```

This is just a shorthand fororder-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanorderutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="order-first md:order-last ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
