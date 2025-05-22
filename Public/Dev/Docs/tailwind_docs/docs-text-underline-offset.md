# https://tailwindcss.com/docs/text-underline-offset

[Original link](https://tailwindcss.com/docs/text-underline-offset)

## Examples

### Basic example

Useunderline-offset-<number>utilities likeunderline-offset-2andunderline-offset-4to change the offset of a text underline:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="underline underline-offset-1">The quick brown fox...</p><p class="underline underline-offset-2">The quick brown fox...</p><p class="underline underline-offset-4">The quick brown fox...</p><p class="underline underline-offset-8">The quick brown fox...</p>
```

### Using a custom value

Use theunderline-offset-[<value>]syntaxto set thetext underline offsetbased on a completely custom value:

```
<p class="underline-offset-[3px] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use theunderline-offset-(<custom-property>)syntax:

```
<p class="underline-offset-(--my-underline-offset) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forunderline-offset-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatext-underline-offsetutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="underline md:underline-offset-4 ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
