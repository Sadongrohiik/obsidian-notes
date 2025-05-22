# https://tailwindcss.com/docs/columns

[Original link](https://tailwindcss.com/docs/columns)

## Examples

### Setting by number

Usecolumns-<number>utilities likecolumns-3to set the number of columns that should be created for the content within an element:

```
<div class="columns-3 ...">  <img class="aspect-3/2 ..." src="/img/mountains-1.jpg" />  <img class="aspect-square ..." src="/img/mountains-2.jpg" />  <img class="aspect-square ..." src="/img/mountains-3.jpg" />  <!-- ... --></div>
```

The column width will automatically adjust to accommodate the specified number of columns.

### Setting by width

Use utilities likecolumns-xsandcolumns-smto set the ideal column width for the content within an element:

Resize the example to see the expected behavior

```
<div class="columns-3xs ...">  <img class="aspect-3/2 ..." src="/img/mountains-1.jpg" />  <img class="aspect-square ..." src="/img/mountains-2.jpg" />  <img class="aspect-square ..." src="/img/mountains-3.jpg" />  <!-- ... --></div>
```

When setting the column width, the number of columns automatically adjusts to ensure they don't get too narrow.

### Setting the column gap

Use thegap-<width>utilities to specify the width between columns:

```
<div class="columns-3 gap-8 ...">  <img class="aspect-3/2 ..." src="/img/mountains-1.jpg" />  <img class="aspect-square ..." src="/img/mountains-2.jpg" />  <img class="aspect-square ..." src="/img/mountains-3.jpg" />  <!-- ... --></div>
```

Learn more about the gap utilities in thegap documentation.

### Using a custom value

Use thecolumns-[<value>]syntaxto set thecolumnsbased on a completely custom value:

```
<div class="columns-[30vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thecolumns-(<custom-property>)syntax:

```
<div class="columns-(--my-columns) ...">  <!-- ... --></div>
```

This is just a shorthand forcolumns-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixacolumnsutilitywith a breakpoint variant likesm:to only apply the utility atsmallscreen sizes and above:

Resize the example to see the expected behavior

```
<div class="columns-2 gap-4 sm:columns-3 sm:gap-8 ...">  <img class="aspect-3/2 ..." src="/img/mountains-1.jpg" />  <img class="aspect-square ..." src="/img/mountains-2.jpg" />  <img class="aspect-square ..." src="/img/mountains-3.jpg" />  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--container-*theme variables to customize thefixed-width columnutilities in your project:

```
@theme {  --container-4xs: 14rem; }
```

Now thecolumns-4xsutility can be used in your markup:

```
<div class="columns-4xs">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
