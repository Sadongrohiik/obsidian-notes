# https://tailwindcss.com/docs/filter-invert

[Original link](https://tailwindcss.com/docs/filter-invert)

## Examples

### Basic example

Use utilities likeinvertandinvert-20to control the color inversion of an element:

invert-0

invert-20

invert

```
<img class="invert-0" src="/img/mountains.jpg" /><img class="invert-20" src="/img/mountains.jpg" /><img class="invert" src="/img/mountains.jpg" />
```

### Using a custom value

Use theinvert-[<value>]syntaxto set thecolor inversionbased on a completely custom value:

```
<img class="invert-[.25] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use theinvert-(<custom-property>)syntax:

```
<img class="invert-(--my-inversion) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forinvert-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: invert()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="invert md:invert-0 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
