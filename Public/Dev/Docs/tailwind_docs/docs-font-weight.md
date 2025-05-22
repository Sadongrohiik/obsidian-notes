# https://tailwindcss.com/docs/font-weight

[Original link](https://tailwindcss.com/docs/font-weight)

## Examples

### Basic example

Use utilities likefont-thinandfont-boldto set the font weight of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="font-light ...">The quick brown fox ...</p><p class="font-normal ...">The quick brown fox ...</p><p class="font-medium ...">The quick brown fox ...</p><p class="font-semibold ...">The quick brown fox ...</p><p class="font-bold ...">The quick brown fox ...</p>
```

### Using a custom value

Use thefont-[<value>]syntaxto set thefont weightbased on a completely custom value:

```
<p class="font-[1000] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thefont-(<custom-property>)syntax:

```
<p class="font-(--my-font-weight) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forfont-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafont-weightutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="font-normal md:font-bold ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--font-weight-*theme variables to customize thefont weightutilities in your project:

```
@theme {  --font-weight-extrablack: 1000; }
```

Now thefont-extrablackutility can be used in your markup:

```
<div class="font-extrablack">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
