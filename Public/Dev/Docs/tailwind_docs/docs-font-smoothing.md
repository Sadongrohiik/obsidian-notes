# https://tailwindcss.com/docs/font-smoothing

[Original link](https://tailwindcss.com/docs/font-smoothing)

## Examples

### Grayscale antialiasing

Use theantialiasedutility to render text using grayscale antialiasing:

The quick brown fox jumps over the lazy dog.

```
<p class="antialiased ...">The quick brown fox ...</p>
```

### Subpixel antialiasing

Use thesubpixel-antialiasedutility to render text using subpixel antialiasing:

The quick brown fox jumps over the lazy dog.

```
<p class="subpixel-antialiased ...">The quick brown fox ...</p>
```

### Responsive design

Prefix-webkit-font-smoothingand-moz-osx-font-smoothingutilitieswith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="antialiased md:subpixel-antialiased ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
