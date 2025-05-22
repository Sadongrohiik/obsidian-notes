# https://tailwindcss.com/docs/transition-property

[Original link](https://tailwindcss.com/docs/transition-property)

## Examples

### Basic example

Use utilities liketransitionandtransition-colorsto specify which properties should transition when they change:

Hover the button to see the expected behavior

```
<button class="bg-blue-500 transition delay-150 duration-300 ease-in-out hover:-translate-y-1 hover:scale-110 hover:bg-indigo-500 ...">  Save Changes</button>
```

### Supporting reduced motion

For situations where the user has specified that they prefer reduced motion, you can conditionally apply animations and transitions using themotion-safeandmotion-reducevariants:

```
<button class="transform transition hover:-translate-y-1 motion-reduce:transition-none motion-reduce:hover:transform-none ...">  <!-- ... --></button>
```

### Using a custom value

Use thetransition-[<value>]syntaxto set thetransition propertiesbased on a completely custom value:

```
<button class="transition-[height] ...">  <!-- ... --></button>
```

For CSS variables, you can also use thetransition-(<custom-property>)syntax:

```
<button class="transition-(--my-properties) ...">  <!-- ... --></button>
```

This is just a shorthand fortransition-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatransition-propertyutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="transition-none md:transition-all ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.
