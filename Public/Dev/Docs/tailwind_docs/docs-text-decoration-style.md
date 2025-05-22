# https://tailwindcss.com/docs/text-decoration-style

[Original link](https://tailwindcss.com/docs/text-decoration-style)

## Examples

### Basic example

Use utilities likedecoration-dottedanddecoration-dashedto change thetext decorationstyle of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="underline decoration-solid">The quick brown fox...</p><p class="underline decoration-double">The quick brown fox...</p><p class="underline decoration-dotted">The quick brown fox...</p><p class="underline decoration-dashed">The quick brown fox...</p><p class="underline decoration-wavy">The quick brown fox...</p>
```

### Responsive design

Prefixatext-decoration-styleutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="underline md:decoration-dashed ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
