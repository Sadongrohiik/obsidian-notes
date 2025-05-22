# https://tailwindcss.com/docs/transition-timing-function

[Original link](https://tailwindcss.com/docs/transition-timing-function)

## Examples

### Basic example

Use utilities likeease-inandease-outto control the easing curve of an element's transition:

Hover each button to see the expected behavior

ease-in

ease-out

ease-in-out

```
<button class="duration-300 ease-in ...">Button A</button><button class="duration-300 ease-out ...">Button B</button><button class="duration-300 ease-in-out ...">Button C</button>
```

### Using a custom value

Use theease-[<value>]syntaxto set thetransition timing functionbased on a completely custom value:

```
<button class="ease-[cubic-bezier(0.95,0.05,0.795,0.035)] ...">  <!-- ... --></button>
```

For CSS variables, you can also use theease-(<custom-property>)syntax:

```
<button class="ease-(--my-ease) ...">  <!-- ... --></button>
```

This is just a shorthand forease-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatransition-timing-functionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="ease-out md:ease-in ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--ease-*theme variables to customize thetransition timing functionutilities in your project:

```
@theme {  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035); }
```

Now theease-in-expoutility can be used in your markup:

```
<button class="ease-in-expo">  <!-- ... --></button>
```

Learn more about customizing your theme in thetheme documentation.
