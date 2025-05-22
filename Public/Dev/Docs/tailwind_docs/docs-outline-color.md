# https://tailwindcss.com/docs/outline-color

[Original link](https://tailwindcss.com/docs/outline-color)

## Examples

### Basic example

Use utilities likeoutline-rose-500andoutline-lime-100to control the color of an element's outline:

outline-blue-500

outline-cyan-500

outline-pink-500

```
<button class="outline-2 outline-offset-2 outline-blue-500 ...">Button A</button><button class="outline-2 outline-offset-2 outline-cyan-500 ...">Button B</button><button class="outline-2 outline-offset-2 outline-pink-500 ...">Button C</button>
```

### Changing the opacity

Use the color opacity modifier to control the opacity of an element's outline color:

outline-blue-500/100

outline-blue-500/75

outline-blue-500/50

```
<button class="outline-2 outline-blue-500/100 ...">Button A</button><button class="outline-2 outline-blue-500/75 ...">Button B</button><button class="outline-2 outline-blue-500/50 ...">Button C</button>
```

### Using a custom value

Use theoutline-[<value>]syntaxto set theoutline colorbased on a completely custom value:

```
<div class="outline-[#243c5a] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theoutline-(<custom-property>)syntax:

```
<div class="outline-(--my-color) ...">  <!-- ... --></div>
```

This is just a shorthand foroutline-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanoutline-colorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="outline md:outline-blue-400 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now theoutline-regal-blueutility can be used in your markup:

```
<div class="outline-regal-blue">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
