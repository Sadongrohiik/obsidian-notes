# https://tailwindcss.com/docs/filter-blur

[Original link](https://tailwindcss.com/docs/filter-blur)

## Examples

### Basic example

Use utilities likeblur-smandblur-lgto blur an element:

blur-none

blur-sm

blur-lg

blur-2xl

```
<img class="blur-none" src="/img/mountains.jpg" /><img class="blur-sm" src="/img/mountains.jpg" /><img class="blur-lg" src="/img/mountains.jpg" /><img class="blur-2xl" src="/img/mountains.jpg" />
```

### Using a custom value

Use theblur-[<value>]syntaxto set theblurbased on a completely custom value:

```
<img class="blur-[2px] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use theblur-(<custom-property>)syntax:

```
<img class="blur-(--my-blur) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forblur-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafilter: blur()utilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="blur-none md:blur-lg ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--blur-*theme variables to customize theblurutilities in your project:

```
@theme {  --blur-2xs: 2px; }
```

Now theblur-2xsutility can be used in your markup:

```
<img class="blur-2xs" src="/img/mountains.jpg" />
```

Learn more about customizing your theme in thetheme documentation.
