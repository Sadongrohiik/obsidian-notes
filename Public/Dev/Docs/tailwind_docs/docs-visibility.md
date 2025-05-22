# https://tailwindcss.com/docs/visibility

[Original link](https://tailwindcss.com/docs/visibility)

## Examples

### Making elements invisible

Use theinvisibleutility to hide an element, but still maintain its place in the document, affecting the layout of other elements:

```
<div class="grid grid-cols-3 gap-4">  <div>01</div>  <div class="invisible ...">02</div>  <div>03</div></div>
```

To completely remove an element from the document, use thedisplayproperty instead.

### Collapsing elements

Use thecollapseutility to hide table rows, row groups, columns, and column groups as if they were set todisplay: none, but without impacting the size of other rows and columns:

```
<table>  <thead>    <tr>      <th>Invoice #</th>      <th>Client</th>      <th>Amount</th>    </tr>  </thead>  <tbody>    <tr>      <td>#100</td>      <td>Pendant Publishing</td>      <td>$2,000.00</td>    </tr>    <tr class="collapse">      <td>#101</td>      <td>Kruger Industrial Smoothing</td>      <td>$545.00</td>    </tr>    <tr>      <td>#102</td>      <td>J. Peterman</td>      <td>$10,000.25</td>    </tr>  </tbody></table>
```

This makes it possible to dynamically toggle rows and columns without affecting the table layout.

### Making elements visible

Use thevisibleutility to make an element visible:

```
<div class="grid grid-cols-3 gap-4">  <div>01</div>  <div class="visible ...">02</div>  <div>03</div></div>
```

This is mostly useful for undoing theinvisibleutility at different screen sizes.

### Responsive design

Prefixavisibilityutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="visible md:invisible ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
