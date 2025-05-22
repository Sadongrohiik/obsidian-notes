# https://tailwindcss.com/docs/outline-width

[Original link](https://tailwindcss.com/docs/outline-width)

## Examples

### Basic example

Useoutlineoroutline-<number>utilities likeoutline-2andoutline-4to set the width of an element's outline:

outline

outline-2

outline-4

```
<button class="outline outline-offset-2 ...">Button A</button><button class="outline-2 outline-offset-2 ...">Button B</button><button class="outline-4 outline-offset-2 ...">Button C</button>
```

### Applying on focus

Prefixanoutline-widthutility with a variant likefocus:*to only apply the utility in that state:

Focus the button to see the outline added

```
<button class="outline-offset-2 outline-sky-500 focus:outline-2 ...">Save Changes</button>
```

Learn more about using variants in thevariants documentation.

### Using a custom value

Use theoutline-[<value>]syntaxto set theoutline widthbased on a completely custom value:

```
<div class="outline-[2vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theoutline-(length:<custom-property>)syntax:

```
<div class="outline-(length:--my-outline-width) ...">  <!-- ... --></div>
```

This is just a shorthand foroutline-[length:var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanoutline-widthutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="outline md:outline-2 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
