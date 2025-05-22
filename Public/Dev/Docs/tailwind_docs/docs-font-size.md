# https://tailwindcss.com/docs/font-size

[Original link](https://tailwindcss.com/docs/font-size)

## Examples

### Basic example

Use utilities liketext-smandtext-lgto set the font size of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="text-sm ...">The quick brown fox ...</p><p class="text-base ...">The quick brown fox ...</p><p class="text-lg ...">The quick brown fox ...</p><p class="text-xl ...">The quick brown fox ...</p><p class="text-2xl ...">The quick brown fox ...</p>
```

### Setting the line-height

Use utilities liketext-sm/6andtext-lg/7to set the font size and line-height of an element at the same time:

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

```
<p class="text-sm/6 ...">So I started to walk into the water...</p><p class="text-sm/7 ...">So I started to walk into the water...</p><p class="text-sm/8 ...">So I started to walk into the water...</p>
```

### Using a custom value

Use thetext-[<value>]syntaxto set thefont sizebased on a completely custom value:

```
<p class="text-[14px] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thetext-(length:<custom-property>)syntax:

```
<p class="text-(length:--my-text-size) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand fortext-[length:var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafont-sizeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="text-sm md:text-base ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--text-*theme variables to customize thefont sizeutilities in your project:

```
@theme {  --text-tiny: 0.625rem; }
```

Now thetext-tinyutility can be used in your markup:

```
<div class="text-tiny">  <!-- ... --></div>
```

You can also provide defaultline-height,letter-spacing, andfont-weightvalues for a font size:

```
@theme {  --text-tiny: 0.625rem;  --text-tiny--line-height: 1.5rem;   --text-tiny--letter-spacing: 0.125rem;   --text-tiny--font-weight: 500; }
```

Learn more about customizing your theme in thetheme documentation.
