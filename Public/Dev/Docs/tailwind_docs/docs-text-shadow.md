# https://tailwindcss.com/docs/text-shadow

[Original link](https://tailwindcss.com/docs/text-shadow)

## Examples

### Basic example

Use utilities liketext-shadow-smandshadow-lgto apply different sized text shadows to a text element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="text-shadow-2xs ...">The quick brown fox...</p><p class="text-shadow-xs ...">The quick brown fox...</p><p class="text-shadow-sm ...">The quick brown fox...</p><p class="text-shadow-md ...">The quick brown fox...</p><p class="text-shadow-lg ...">The quick brown fox...</p>
```

### Changing the opacity

Use the opacity modifier to adjust the opacity of the text shadow:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="text-shadow-lg ...">The quick brown fox...</p><p class="text-shadow-lg/20 ...">The quick brown fox...</p><p class="text-shadow-lg/30 ...">The quick brown fox...</p>
```

The default text shadow opacities are quite low (20% or less), so increasing the opacity (to like 50%) will make the text shadows more pronounced.

### Setting the shadow color

Use utilities liketext-shadow-indigo-500andtext-shadow-cyan-500/50to change the color of a text shadow:

```
<button class="text-sky-950 text-shadow-2xs text-shadow-sky-300 ...">Book a demo</button><button class="text-gray-950 dark:text-white dark:text-shadow-2xs ...">See pricing</button>
```

By default colored shadows have an opacity of 100% but you can adjust this using the opacity modifier.

### Removing a text shadow

Use thetext-shadow-noneutility to remove an existing text shadow from an element:

```
<p class="text-shadow-lg dark:text-shadow-none">  <!-- ... --></p>
```

### Using a custom value

Use thetext-shadow-[<value>]syntaxto set thetext shadowbased on a completely custom value:

```
<p class="text-shadow-[0_35px_35px_rgb(0_0_0_/_0.25)] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thetext-shadow-(<custom-property>)syntax:

```
<p class="text-shadow-(--my-text-shadow) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand fortext-shadow-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatext-shadowutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="text-shadow-none md:text-shadow-lg ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

### Customizing text shadows

Use the--text-shadow-*theme variables to customize thetext shadowutilities in your project:

```
@theme {  --text-shadow-xl: 0 35px 35px rgb(0, 0, 0 / 0.25); }
```

Now thetext-shadow-xlutility can be used in your markup:

```
<p class="text-shadow-xl">  Lorem ipsum dolor sit amet...</p>
```

Learn more about customizing your theme in thetheme documentation.

### Customizing shadow colors

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thetext-shadow-regal-blueutility can be used in your markup:

```
<p class="text-shadow-regal-blue">  Lorem ipsum dolor sit amet...</p>
```

Learn more about customizing your theme in thetheme documentation.
