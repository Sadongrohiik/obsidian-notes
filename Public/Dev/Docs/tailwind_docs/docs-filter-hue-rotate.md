# https://tailwindcss.com/docs/filter-hue-rotate

[Original link](https://tailwindcss.com/docs/filter-hue-rotate)

## Examples

### Basic example

Use utilities likehue-rotate-90andhue-rotate-180to rotate the hue of an element by degrees:

hue-rotate-15

hue-rotate-90

hue-rotate-180

hue-rotate-270

```
<img class="hue-rotate-15" src="/img/mountains.jpg" /><img class="hue-rotate-90" src="/img/mountains.jpg" /><img class="hue-rotate-180" src="/img/mountains.jpg" /><img class="hue-rotate-270" src="/img/mountains.jpg" />
```

### Using negative values

Use utilities like-hue-rotate-15and-hue-rotate-45to set a negative hue rotate value:

-hue-rotate-15

-hue-rotate-45

-hue-rotate-90

```
<img class="-hue-rotate-15" src="/img/mountains.jpg" /><img class="-hue-rotate-45" src="/img/mountains.jpg" /><img class="-hue-rotate-90" src="/img/mountains.jpg" />
```

### Using a custom value

Use thehue-rotate-[<value>]syntaxto set thehue rotationbased on a completely custom value:

```
<img class="hue-rotate-[3.142rad] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thehue-rotate-(<custom-property>)syntax:

```
<img class="hue-rotate-(--my-hue-rotate) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forhue-rotate-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: hue-rotate()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="hue-rotate-60 md:hue-rotate-0 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
