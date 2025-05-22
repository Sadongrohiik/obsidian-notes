# https://tailwindcss.com/docs/list-style-image

[Original link](https://tailwindcss.com/docs/list-style-image)

## Examples

### Basic example

Use thelist-image-[<value>]syntax to control the marker image for list items:

```
<ul class="list-image-[url(/img/checkmark.png)]">  <li>5 cups chopped Porcini mushrooms</li>  <!-- ... --></ul>
```

### Using a CSS variable

Use thelist-image-(<custom-property>)syntax to control the marker image for list items using a CSS variable:

```
<ul class="list-image-(--my-list-image)">  <!-- ... --></ul>
```

This is just a shorthand forlist-image-[var(<custom-property>)]that adds thevar()function for you automatically.

### Removing a marker image

Use thelist-image-noneutility to remove an existing marker image from list items:

```
<ul class="list-image-none">  <!-- ... --></ul>
```

### Responsive design

Prefixalist-style-imageutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="list-image-none md:list-image-[url(/img/checkmark.png)] ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
