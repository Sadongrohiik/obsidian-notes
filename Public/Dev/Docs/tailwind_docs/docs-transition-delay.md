# https://tailwindcss.com/docs/transition-delay

[Original link](https://tailwindcss.com/docs/transition-delay)

## Examples

### Basic example

Use utilities likedelay-150anddelay-700to set the transition delay of an element in milliseconds:

Hover each button to see the expected behavior

delay-150

delay-300

delay-700

```
<button class="transition delay-150 duration-300 ease-in-out ...">Button A</button><button class="transition delay-300 duration-300 ease-in-out ...">Button B</button><button class="transition delay-700 duration-300 ease-in-out ...">Button C</button>
```

### Using a custom value

Use thedelay-[<value>]syntaxto set thetransition delaybased on a completely custom value:

```
<button class="delay-[1s,250ms] ...">  <!-- ... --></button>
```

For CSS variables, you can also use thedelay-(<custom-property>)syntax:

```
<button class="delay-(--my-delay) ...">  <!-- ... --></button>
```

This is just a shorthand fordelay-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatransition-delayutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="delay-150 md:delay-300 ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.
