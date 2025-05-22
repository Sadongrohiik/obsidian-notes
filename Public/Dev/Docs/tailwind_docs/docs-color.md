# https://tailwindcss.com/docs/color

[Original link](https://tailwindcss.com/docs/color)

## Examples

### Basic example

Use utilities liketext-blue-600andtext-sky-400to control the text color of an element:

The quick brown fox jumps over the lazy dog.

```
<p class="text-blue-600 dark:text-sky-400">The quick brown fox...</p>
```

### Changing the opacity

Use the color opacity modifier to control the text color opacity of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="text-blue-600/100 dark:text-sky-400/100">The quick brown fox...</p><p class="text-blue-600/75 dark:text-sky-400/75">The quick brown fox...</p><p class="text-blue-600/50 dark:text-sky-400/50">The quick brown fox...</p><p class="text-blue-600/25 dark:text-sky-400/25">The quick brown fox...</p>
```

### Using a custom value

Use thetext-[<value>]syntaxto set thetext colorbased on a completely custom value:

```
<p class="text-[#50d71e] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thetext-(<custom-property>)syntax:

```
<p class="text-(--my-color) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand fortext-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixacolorutility with a variant likehover:*to only apply the utility in that state:

Hover over the text to see the expected behavior

Oh I gotta get on thatinternet, I'm late on everything!

```
<p class="...">  Oh I gotta get on that  <a class="underline hover:text-blue-600 dark:hover:text-blue-400" href="https://en.wikipedia.org/wiki/Internet">internet</a>,  I'm late on everything!</p>
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixacolorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="text-blue-600 md:text-green-600 ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thetext-regal-blueutility can be used in your markup:

```
<p class="text-regal-blue">  Lorem ipsum dolor sit amet...</p>
```

Learn more about customizing your theme in thetheme documentation.
