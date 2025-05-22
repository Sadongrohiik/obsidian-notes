# https://tailwindcss.com/docs/filter-saturate

[Original link](https://tailwindcss.com/docs/filter-saturate)

## Examples

### Basic example

Use utilities likesaturate-50andsaturate-100to control an element's saturation:

saturate-50

saturate-100

saturate-150

saturate-200

```
<img class="saturate-50 ..." src="/img/mountains.jpg" /><img class="saturate-100 ..." src="/img/mountains.jpg" /><img class="saturate-150 ..." src="/img/mountains.jpg" /><img class="saturate-200 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use thesaturate-[<value>]syntaxto set thesaturationbased on a completely custom value:

```
<img class="saturate-[.25] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thesaturate-(<custom-property>)syntax:

```
<img class="saturate-(--my-saturation) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forsaturate-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: saturate()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="saturate-50 md:saturate-150 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
