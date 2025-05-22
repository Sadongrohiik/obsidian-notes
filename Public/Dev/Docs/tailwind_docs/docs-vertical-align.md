# https://tailwindcss.com/docs/vertical-align

[Original link](https://tailwindcss.com/docs/vertical-align)

## Examples

### Aligning to baseline

Use thealign-baselineutility to align the baseline of an element with the baseline of its parent:

```
<span class="inline-block align-baseline">The quick brown fox...</span>
```

### Aligning to top

Use thealign-toputility to align the top of an element and its descendants with the top of the entire line:

```
<span class="inline-block align-top">The quick brown fox...</span>
```

### Aligning to middle

Use thealign-middleutility to align the middle of an element with the baseline plus half the x-height of the parent:

```
<span class="inline-block align-middle">The quick brown fox...</span>
```

### Aligning to bottom

Use thealign-bottomutility to align the bottom of an element and its descendants with the bottom of the entire line:

```
<span class="inline-block align-bottom">The quick brown fox...</span>
```

### Aligning to parent top

Use thealign-text-toputility to align the top of an element with the top of the parent element's font:

```
<span class="inline-block align-text-top">The quick brown fox...</span>
```

### Aligning to parent bottom

Use thealign-text-bottomutility to align the bottom of an element with the bottom of the parent element's font:

```
<span class="inline-block align-text-bottom">The quick brown fox...</span>
```

### Using a custom value

Use thealign-[<value>]syntaxto set thevertical alignmentbased on a completely custom value:

```
<span class="align-[4px] ...">  <!-- ... --></span>
```

For CSS variables, you can also use thealign-(<custom-property>)syntax:

```
<span class="align-(--my-alignment) ...">  <!-- ... --></span>
```

This is just a shorthand foralign-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixavertical-alignutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<span class="align-middle md:align-top ...">  <!-- ... --></span>
```

Learn more about using variants in thevariants documentation.
