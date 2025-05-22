# https://tailwindcss.com/docs/accent-color

[Original link](https://tailwindcss.com/docs/accent-color)

## Examples

### Setting the accent color

Use utilities likeaccent-rose-500andaccent-lime-600to change the accent color of an element:

```
<label>  <input type="checkbox" checked />  Browser default</label><label>  <input class="accent-pink-500" type="checkbox" checked />  Customized</label>
```

This is helpful for styling elements like checkboxes and radio groups by overriding the browser's default color.

### Changing the opacity

Use the color opacity modifier to control the opacity of an element's accent color:

```
<input class="accent-purple-500/25" type="checkbox" checked /><input class="accent-purple-500/75" type="checkbox" checked />
```

Setting the accent color opacity has limited browser-support and only works in Firefox at this time.

### Using a custom value

Use theaccent-[<value>]syntaxto set theaccent colorbased on a completely custom value:

```
<input class="accent-[#50d71e] ..." type="checkbox" />
```

For CSS variables, you can also use theaccent-(<custom-property>)syntax:

```
<input class="accent-(--my-accent-color) ..." type="checkbox" />
```

This is just a shorthand foraccent-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixanaccent-colorutility with a variant likehover:*to only apply the utility in that state:

```
<input class="accent-black hover:accent-pink-500" type="checkbox" />
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixanaccent-colorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<input class="accent-black md:accent-pink-500 ..." type="checkbox" />
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now theaccent-regal-blueutility can be used in your markup:

```
<input class="accent-regal-blue" type="checkbox" />
```

Learn more about customizing your theme in thetheme documentation.
