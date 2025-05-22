# https://tailwindcss.com/docs/transition-duration

[Original link](https://tailwindcss.com/docs/transition-duration)

## Examples

### Basic example

Use utilities likeduration-150andduration-700to set the transition duration of an element in milliseconds:

Hover each button to see the expected behavior

duration-150

duration-300

duration-700

```
<button class="transition duration-150 ease-in-out ...">Button A</button><button class="transition duration-300 ease-in-out ...">Button B</button><button class="transition duration-700 ease-in-out ...">Button C</button>
```

### Using a custom value

Use theduration-[<value>]syntaxto set thetransition durationbased on a completely custom value:

```
<button class="duration-[1s,15s] ...">  <!-- ... --></button>
```

For CSS variables, you can also use theduration-(<custom-property>)syntax:

```
<button class="duration-(--my-duration) ...">  <!-- ... --></button>
```

This is just a shorthand forduration-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatransition-durationutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="duration-0 md:duration-150 ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.
