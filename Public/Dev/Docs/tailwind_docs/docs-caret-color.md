# https://tailwindcss.com/docs/caret-color

[Original link](https://tailwindcss.com/docs/caret-color)

## Examples

### Basic example

Use utilities likecaret-rose-500andcaret-lime-600to change the color of the text input cursor:

Focus the textarea to see the new caret color

```
<textarea class="caret-pink-500 ..."></textarea>
```

### Using a custom value

Use thecaret-[<value>]syntaxto set thecaret colorbased on a completely custom value:

```
<textarea class="caret-[#50d71e] ..."></textarea>
```

For CSS variables, you can also use thecaret-(<custom-property>)syntax:

```
<textarea class="caret-(--my-caret-color) ..."></textarea>
```

This is just a shorthand forcaret-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixacaret-colorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<textarea class="caret-rose-500 md:caret-lime-600 ..."></textarea>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now thecaret-regal-blueutility can be used in your markup:

```
<textarea class="caret-regal-blue"></textarea>
```

Learn more about customizing your theme in thetheme documentation.
