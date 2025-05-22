# https://tailwindcss.com/docs/filter-grayscale

[Original link](https://tailwindcss.com/docs/filter-grayscale)

## Examples

### Basic example

Use utilities likegrayscaleandgrayscale-75to control the amount of grayscale effect applied to an element:

grayscale-0

grayscale-25

grayscale-50

grayscale

```
<img class="grayscale-0 ..." src="/img/mountains.jpg" /><img class="grayscale-25 ..." src="/img/mountains.jpg" /><img class="grayscale-50 ..." src="/img/mountains.jpg" /><img class="grayscale ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use thegrayscale-[<value>]syntaxto set thegrayscalebased on a completely custom value:

```
<img class="grayscale-[0.5] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thegrayscale-(<custom-property>)syntax:

```
<img class="grayscale-(--my-grayscale) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forgrayscale-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: grayscale()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="grayscale md:grayscale-0 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
