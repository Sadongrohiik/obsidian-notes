# https://tailwindcss.com/docs/font-family

[Original link](https://tailwindcss.com/docs/font-family)

## Examples

### Basic example

Use utilities likefont-sansandfont-monoto set the font family of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="font-sans ...">The quick brown fox ...</p><p class="font-serif ...">The quick brown fox ...</p><p class="font-mono ...">The quick brown fox ...</p>
```

### Using a custom value

Use thefont-[<value>]syntaxto set thefont familybased on a completely custom value:

```
<p class="font-[Open_Sans] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thefont-(family-name:<custom-property>)syntax:

```
<p class="font-(family-name:--my-font) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forfont-[family-name:var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixafont-familyutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="font-sans md:font-serif ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--font-*theme variables to customize thefont familyutilities in your project:

```
@theme {  --font-display: "Oswald", "sans-serif"; }
```

Now thefont-displayutility can be used in your markup:

```
<div class="font-display">  <!-- ... --></div>
```

You can also provide defaultfont-feature-settingsandfont-variation-settingsvalues for a font family:

```
@theme {  --font-display: "Oswald", "sans-serif";  --font-display--font-feature-settings: "cv02", "cv03", "cv04", "cv11";   --font-display--font-variation-settings: "opsz" 32; }
```

If needed, use the@font-faceat-rule to load custom fonts:

```
@font-face {  font-family: Oswald;  font-style: normal;  font-weight: 200 700;  font-display: swap;  src: url("/fonts/Oswald.woff2") format("woff2");}
```

If you're loading a font from a service likeGoogle Fonts, make sure to put the@importat the very top of your CSS file:

```
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");@import "tailwindcss";@theme {  --font-roboto: "Roboto", sans-serif; }
```

Browsers require that@importstatements come before any other rules, so URL imports need to be above imports like@import "tailwindcss"which are inlined in the compiled CSS.

Learn more about customizing your theme in thetheme documentation.
