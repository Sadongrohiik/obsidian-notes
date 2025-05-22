# https://tailwindcss.com/docs/font-stretch

[Original link](https://tailwindcss.com/docs/font-stretch)

## Examples

### Basic example

Use utilities likefont-stretch-condensedandfont-stretch-expandedto set the width of a font face:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="font-stretch-extra-condensed">The quick brown fox...</p><p class="font-stretch-condensed">The quick brown fox...</p><p class="font-stretch-normal">The quick brown fox...</p><p class="font-stretch-expanded">The quick brown fox...</p><p class="font-stretch-extra-expanded">The quick brown fox...</p>
```

This only applies to fonts that have multiple width variations available, otherwise the browser selects the closest match.

### Using percentages

Usefont-stretch-<percentage>utilities likefont-stretch-50%andfont-stretch-125%to set the width of a font face using a percentage:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="font-stretch-50%">The quick brown fox...</p><p class="font-stretch-100%">The quick brown fox...</p><p class="font-stretch-150%">The quick brown fox...</p>
```

### Using a custom value

Use thefont-stretch-[<value>]syntaxto set thefont widthbased on a completely custom value:

```
<p class="font-stretch-[66.66%] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thefont-stretch-(<custom-property>)syntax:

```
<p class="font-stretch-(--my-font-width) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forfont-stretch-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafont-stretchutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="font-stretch-normal md:font-stretch-expanded ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
