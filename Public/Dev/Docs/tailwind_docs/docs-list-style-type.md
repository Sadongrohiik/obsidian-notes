# https://tailwindcss.com/docs/list-style-type

[Original link](https://tailwindcss.com/docs/list-style-type)

## Examples

### Basic example

Use utilities likelist-discandlist-decimalto control the style of the markers in a list:

```
<ul class="list-disc">  <li>Now this is a story all about how, my life got flipped-turned upside down</li>  <!-- ... --></ul><ol class="list-decimal">  <li>Now this is a story all about how, my life got flipped-turned upside down</li>  <!-- ... --></ol><ul class="list-none">  <li>Now this is a story all about how, my life got flipped-turned upside down</li>  <!-- ... --></ul>
```

### Using a custom value

Use thelist-[<value>]syntaxto set themarkerbased on a completely custom value:

```
<ol class="list-[upper-roman] ...">  <!-- ... --></ol>
```

For CSS variables, you can also use thelist-(<custom-property>)syntax:

```
<ol class="list-(--my-marker) ...">  <!-- ... --></ol>
```

This is just a shorthand forlist-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixalist-style-typeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<ul class="list-none md:list-disc ...">  <!-- ... --></ul>
```

Learn more about using variants in thevariants documentation.
