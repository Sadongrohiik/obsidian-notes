# https://tailwindcss.com/docs/text-transform

[Original link](https://tailwindcss.com/docs/text-transform)

## Examples

### Uppercasing text

Use theuppercaseutility to uppercase the text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="uppercase">The quick brown fox ...</p>
```

### Lowercasing text

Use thelowercaseutility to lowercase the text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="lowercase">The quick brown fox ...</p>
```

### Capitalizing text

Use thecapitalizeutility to capitalize text of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="capitalize">The quick brown fox ...</p>
```

### Resetting text casing

Use thenormal-caseutility to preserve the original text casing of an element—typically used to reset capitalization at different breakpoints:

The quick brown fox jumps over the lazy dog.

```
<p class="normal-case">The quick brown fox ...</p>
```

### Responsive design

Prefixatext-transformutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="capitalize md:uppercase ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
