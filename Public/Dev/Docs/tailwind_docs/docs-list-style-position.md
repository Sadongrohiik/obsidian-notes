# https://tailwindcss.com/docs/list-style-position

[Original link](https://tailwindcss.com/docs/list-style-position)

## Examples

### Basic example

Use utilities likelist-insideandlist-outsideto control the position of the markers and text indentation in a list:

list-inside

list-outside

```
<ul class="list-inside">  <li>5 cups chopped Porcini mushrooms</li>  <!-- ... --></ul><ul class="list-outside">  <li>5 cups chopped Porcini mushrooms</li>  <!-- ... --></ul>
```

### Responsive design

Prefixalist-style-positionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<ul class="list-outside md:list-inside ...">  <!-- ... --></ul>
```

Learn more about using variants in thevariants documentation.
