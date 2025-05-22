# https://tailwindcss.com/docs/filter

[Original link](https://tailwindcss.com/docs/filter)

## Examples

### Basic example

Use utilities likeblur-xsandgrayscaleto apply filters to an element:

blur-xs

grayscale

combined

```
<img class="blur-xs" src="/img/mountains.jpg" /><img class="grayscale" src="/img/mountains.jpg" /><img class="blur-xs grayscale" src="/img/mountains.jpg" />
```

You can combine the following filter utilities:blur,brightness,contrast,drop-shadow,grayscale,hue-rotate,invert,saturate, andsepia.

### Removing filters

Use thefilter-noneutility to remove all of the filters applied to an element:

```
<img class="blur-md brightness-150 invert md:filter-none" src="/img/mountains.jpg" />
```

### Using a custom value

Use thefilter-[<value>]syntaxto set thefilterbased on a completely custom value:

```
<img class="filter-[url('filters.svg#filter-id')] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thefilter-(<custom-property>)syntax:

```
<img class="filter-(--my-filter) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forfilter-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixafilterutility with a variant likehover:*to only apply the utility in that state:

```
<img class="blur-sm hover:filter-none ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixafilterutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="blur-sm md:filter-none ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
