# https://tailwindcss.com/docs/z-index

[Original link](https://tailwindcss.com/docs/z-index)

## Examples

### Basic example

Use thez-<number>utilities likez-10andz-50to control the stack order (or three-dimensional positioning) of an element, regardless of the order it has been displayed:

```
<div class="z-40 ...">05</div><div class="z-30 ...">04</div><div class="z-20 ...">03</div><div class="z-10 ...">02</div><div class="z-0 ...">01</div>
```

### Using negative values

To use a negative z-index value, prefix the class name with a dash to convert it to a negative value:

```
<div class="...">05</div><div class="...">04</div><div class="-z-10 ...">03</div><div class="...">02</div><div class="...">01</div>
```

### Using a custom value

Use thez-[<value>]syntaxto set thestack orderbased on a completely custom value:

```
<div class="z-[calc(var(--index)+1)] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thez-(<custom-property>)syntax:

```
<div class="z-(--my-z) ...">  <!-- ... --></div>
```

This is just a shorthand forz-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaz-indexutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="z-0 md:z-50 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
