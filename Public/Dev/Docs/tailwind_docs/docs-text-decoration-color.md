# https://tailwindcss.com/docs/text-decoration-color

[Original link](https://tailwindcss.com/docs/text-decoration-color)

## Examples

### Basic example

Use utilities likedecoration-sky-500anddecoration-pink-500to change thetext decorationcolor of an element:

I’m Derek, an astro-engineer based in Tattooine. I like to build X-Wings atMy Company, Inc. Outside of work, I like towatch pod-racingand havelight-saberfights.

```
<p>  I’m Derek, an astro-engineer based in Tattooine. I like to build X-Wings  at <a class="underline decoration-sky-500">My Company, Inc</a>. Outside  of work, I like to <a class="underline decoration-pink-500">watch pod-racing</a>  and have <a class="underline decoration-indigo-500">light-saber</a> fights.</p>
```

### Changing the opacity

Use the color opacity modifier to control the text decoration color opacity of an element:

I’m Derek, an astro-engineer based in Tattooine. I like to build X-Wings atMy Company, Inc. Outside of work, I like towatch pod-racingand havelight-saberfights.

```
<p>  I’m Derek, an astro-engineer based in Tattooine. I like to build X-Wings  at <a class="underline decoration-sky-500/30">My Company, Inc</a>. Outside  of work, I like to <a class="underline decoration-pink-500/30">watch pod-racing</a>  and have <a class="underline decoration-indigo-500/30">light-saber</a> fights.</p>
```

### Using a custom value

Use thedecoration-[<value>]syntaxto set thetext decoration colorbased on a completely custom value:

```
<p class="decoration-[#50d71e] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thedecoration-(<custom-property>)syntax:

```
<p class="decoration-(--my-color) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand fordecoration-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixatext-decoration-colorutility with a variant likehover:*to only apply the utility in that state:

Hover over the text to see the expected behavior

```
<p>The <a href="..." class="underline hover:decoration-pink-500 ...">quick brown fox</a> jumps over the lazy dog.</p>
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixatext-decoration-colorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="underline decoration-sky-600 md:decoration-blue-400 ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thedecoration-regal-blueutility can be used in your markup:

```
<p class="decoration-regal-blue">  Lorem ipsum dolor sit amet...</p>
```

Learn more about customizing your theme in thetheme documentation.
