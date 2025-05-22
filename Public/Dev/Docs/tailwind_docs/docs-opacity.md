# https://tailwindcss.com/docs/opacity

[Original link](https://tailwindcss.com/docs/opacity)

## Examples

### Basic example

Useopacity-<number>utilities likeopacity-25andopacity-100to set the opacity of an element:

opacity-100

opacity-75

opacity-50

opacity-25

```
<button class="bg-indigo-500 opacity-100 ..."></button><button class="bg-indigo-500 opacity-75 ..."></button><button class="bg-indigo-500 opacity-50 ..."></button><button class="bg-indigo-500 opacity-25 ..."></button>
```

### Applying conditionally

Prefixanopacityutility with a variant likedisabled:*to only apply the utility in that state:

```
<input class="opacity-100 disabled:opacity-75 ..." type="text" />
```

Learn more about using variants in thevariants documentation.

### Using a custom value

Use theopacity-[<value>]syntaxto set theopacitybased on a completely custom value:

```
<button class="opacity-[.67] ...">  <!-- ... --></button>
```

For CSS variables, you can also use theopacity-(<custom-property>)syntax:

```
<button class="opacity-(--my-opacity) ...">  <!-- ... --></button>
```

This is just a shorthand foropacity-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanopacityutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="opacity-50 md:opacity-100 ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.
