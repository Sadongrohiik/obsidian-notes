# https://tailwindcss.com/docs/text-decoration-thickness

[Original link](https://tailwindcss.com/docs/text-decoration-thickness)

## Examples

### Basic example

Usedecoration-<number>utilities likedecoration-2anddecoration-4to change thetext decorationthickness of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="underline decoration-1">The quick brown fox...</p><p class="underline decoration-2">The quick brown fox...</p><p class="underline decoration-4">The quick brown fox...</p>
```

### Using a custom value

Use thedecoration-[<value>]syntaxto set thetext decoration thicknessbased on a completely custom value:

```
<p class="decoration-[0.25rem] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thedecoration-(length:<custom-property>)syntax:

```
<p class="decoration-(length:--my-decoration-thickness) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand fordecoration-[length:var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatext-decoration-thicknessutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="underline md:decoration-4 ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
