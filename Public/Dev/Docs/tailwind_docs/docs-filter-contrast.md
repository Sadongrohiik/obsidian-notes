# https://tailwindcss.com/docs/filter-contrast

[Original link](https://tailwindcss.com/docs/filter-contrast)

## Examples

### Basic example

Use utilities likecontrast-50andcontrast-100to control an element's contrast:

contrast-50

contrast-100

contrast-125

contrast-200

```
<img class="contrast-50 ..." src="/img/mountains.jpg" /><img class="contrast-100 ..." src="/img/mountains.jpg" /><img class="contrast-125 ..." src="/img/mountains.jpg" /><img class="contrast-200 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use thecontrast-[<value>]syntaxto set thecontrastbased on a completely custom value:

```
<img class="contrast-[.25] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thecontrast-(<custom-property>)syntax:

```
<img class="contrast-(--my-contrast) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forcontrast-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: contrast()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="contrast-125 md:contrast-150 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
