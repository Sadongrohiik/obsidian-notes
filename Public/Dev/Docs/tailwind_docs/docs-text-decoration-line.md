# https://tailwindcss.com/docs/text-decoration-line

[Original link](https://tailwindcss.com/docs/text-decoration-line)

## Examples

### Underling text

Use theunderlineutility to add an underline to the text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="underline">The quick brown fox...</p>
```

### Adding an overline to text

Use theoverlineutility to add an overline to the text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="overline">The quick brown fox...</p>
```

### Adding a line through text

Use theline-throughutility to add a line through the text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="line-through">The quick brown fox...</p>
```

### Removing a line from text

Use theno-underlineutility to remove a line from the text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="no-underline">The quick brown fox...</p>
```

### Applying on hover

Prefixatext-decoration-lineutility with a variant likehover:*to only apply the utility in that state:

Hover over the text to see the expected behavior

```
<p>The <a href="..." class="no-underline hover:underline ...">quick brown fox</a> jumps over the lazy dog.</p>
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixatext-decoration-lineutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<a class="no-underline md:underline ..." href="...">  <!-- ... --></a>
```

Learn more about using variants in thevariants documentation.
