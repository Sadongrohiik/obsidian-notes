# https://tailwindcss.com/docs/overflow-wrap

[Original link](https://tailwindcss.com/docs/overflow-wrap)

## Examples

### Wrapping mid-word

Use thewrap-break-wordutility to allow line breaks between letters in a word if needed:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="wrap-break-word">The longest word in any of the major...</p>
```

### Wrapping anywhere

Thewrap-anywhereutility behaves similarly towrap-break-word, except that the browser factors in mid-word line breaks when calculating the intrinsic size of the element:

wrap-break-word

Jay Riemenschneider

jason.riemenschneider@vandelayindustries.com

wrap-anywhere

Jay Riemenschneider

jason.riemenschneider@vandelayindustries.com

```
<div class="flex max-w-sm">  <img class="size-16 rounded-full" src="/img/profile.jpg" />  <div class="wrap-break-word">    <p class="font-medium">Jay Riemenschneider</p>    <p>jason.riemenschneider@vandelayindustries.com</p>  </div></div><div class="flex max-w-sm">  <img class="size-16 rounded-full" src="/img/profile.jpg" />  <div class="wrap-anywhere">    <p class="font-medium">Jay Riemenschneider</p>    <p>jason.riemenschneider@vandelayindustries.com</p>  </div></div>
```

This is useful for wrapping text inside offlexcontainers, where you would usually need to setmin-width: 0on the child element to allow it to shrink below its content size.

### Wrapping normally

Use thewrap-normalutility to only allow line breaks at natural wrapping points, like spaces, hyphens, and punctuation:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="wrap-normal">The longest word in any of the major...</p>
```

### Responsive design

Prefixanoverflow-wraputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="wrap-normal md:wrap-break-word ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
