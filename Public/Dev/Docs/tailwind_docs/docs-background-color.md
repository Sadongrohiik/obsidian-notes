# https://tailwindcss.com/docs/background-color

[Original link](https://tailwindcss.com/docs/background-color)

## Examples

### Basic example

Use utilities likebg-white,bg-indigo-500andbg-transparentto control the background color of an element:

bg-blue-500

bg-cyan-500

bg-pink-500

```
<button class="bg-blue-500 ...">Button A</button><button class="bg-cyan-500 ...">Button B</button><button class="bg-pink-500 ...">Button C</button>
```

### Changing the opacity

Use the color opacity modifier to control the opacity of an element's background color:

bg-sky-500/100

bg-sky-500/75

bg-sky-500/50

```
<button class="bg-sky-500/100 ..."></button><button class="bg-sky-500/75 ..."></button><button class="bg-sky-500/50 ..."></button>
```

### Using a custom value

Use thebg-[<value>]syntaxto set thebackground colorbased on a completely custom value:

```
<div class="bg-[#50d71e] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebg-(<custom-property>)syntax:

```
<div class="bg-(--my-color) ...">  <!-- ... --></div>
```

This is just a shorthand forbg-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixabackground-colorutility with a variant likehover:*to only apply the utility in that state:

```
<button class="bg-indigo-500 hover:bg-fuchsia-500 ...">Save changes</button>
```

Learn more about using variants in thevariants documentation.

### Responsive design

Prefixabackground-colorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-blue-500 md:bg-green-500 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thebg-regal-blueutility can be used in your markup:

```
<div class="bg-regal-blue">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
