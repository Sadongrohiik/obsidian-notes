# https://tailwindcss.com/docs/outline-offset

[Original link](https://tailwindcss.com/docs/outline-offset)

## Examples

### Basic example

Use utilities likeoutline-offset-2andoutline-offset-4to change the offset of an element's outline:

outline-offset-0

outline-offset-2

outline-offset-4

```
<button class="outline-2 outline-offset-0 ...">Button A</button><button class="outline-2 outline-offset-2 ...">Button B</button><button class="outline-2 outline-offset-4 ...">Button C</button>
```

### Using a custom value

Use theoutline-offset-[<value>]syntaxto set theoutline offsetbased on a completely custom value:

```
<div class="outline-offset-[2vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theoutline-offset-(<custom-property>)syntax:

```
<div class="outline-offset-(--my-outline-offset) ...">  <!-- ... --></div>
```

This is just a shorthand foroutline-offset-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanoutline-offsetutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="outline md:outline-offset-2 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
