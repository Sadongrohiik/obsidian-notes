# https://tailwindcss.com/docs/filter-brightness

[Original link](https://tailwindcss.com/docs/filter-brightness)

## Examples

### Basic example

Use utilities likebrightness-50andbrightness-100to control an element's brightness:

brightness-50

brightness-100

brightness-125

brightness-200

```
<img class="brightness-50 ..." src="/img/mountains.jpg" /><img class="brightness-100 ..." src="/img/mountains.jpg" /><img class="brightness-125 ..." src="/img/mountains.jpg" /><img class="brightness-200 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use thebrightness-[<value>]syntaxto set thebrightnessbased on a completely custom value:

```
<img class="brightness-[1.75] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thebrightness-(<custom-property>)syntax:

```
<img class="brightness-(--my-brightness) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forbrightness-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: brightness()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="brightness-110 md:brightness-150 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
