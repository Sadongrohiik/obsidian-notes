# https://tailwindcss.com/docs/filter-sepia

[Original link](https://tailwindcss.com/docs/filter-sepia)

## Examples

### Basic example

Use utilities likesepiaandsepia-50to control the sepia effect applied to an element:

sepia-0

sepia-50

sepia

```
<img class="sepia-0" src="/img/mountains.jpg" /><img class="sepia-50" src="/img/mountains.jpg" /><img class="sepia" src="/img/mountains.jpg" />
```

### Using a custom value

Use thesepia-[<value>]syntaxto set thesepia amountbased on a completely custom value:

```
<img class="sepia-[.25] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thesepia-(<custom-property>)syntax:

```
<img class="sepia-(--my-sepia) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forsepia-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: sepia()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="sepia md:sepia-0 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
