# https://tailwindcss.com/docs/color-scheme

[Original link](https://tailwindcss.com/docs/color-scheme)

## Examples

### Basic example

Use utilities likescheme-lightandscheme-light-darkto control how element should be rendered:

Try switching your system color scheme to see the difference

scheme-light

scheme-dark

scheme-light-dark

```
<div class="scheme-light ...">  <input type="date" /></div><div class="scheme-dark ...">  <input type="date" /></div><div class="scheme-light-dark ...">  <input type="date" /></div>
```

### Applying in dark mode

Prefixacolor-schemeutility with a variant likedark:*to only apply the utility in that state:

```
<html class="scheme-light dark:scheme-dark ...">  <!-- ... --></html>
```

Learn more about using variants in thevariants documentation.
