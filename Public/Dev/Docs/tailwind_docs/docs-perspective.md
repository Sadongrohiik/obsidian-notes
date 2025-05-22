# https://tailwindcss.com/docs/perspective

[Original link](https://tailwindcss.com/docs/perspective)

## Examples

### Basic example

Use utilities likeperspective-normalandperspective-distantto control how close or how far away the z-plane is from the screen:

perspective-dramatic

perspective-normal

```
<div class="size-20 perspective-dramatic ...">  <div class="translate-z-12 rotate-x-0 bg-sky-300/75 ...">1</div>  <div class="-translate-z-12 rotate-y-18 bg-sky-300/75 ...">2</div>  <div class="translate-x-12 rotate-y-90 bg-sky-300/75 ...">3</div>  <div class="-translate-x-12 -rotate-y-90 bg-sky-300/75 ...">4</div>  <div class="-translate-y-12 rotate-x-90 bg-sky-300/75 ...">5</div>  <div class="translate-y-12 -rotate-x-90 bg-sky-300/75 ...">6</div></div><div class="size-20 perspective-normal ...">  <div class="translate-z-12 rotate-x-0 bg-sky-300/75 ...">1</div>  <div class="-translate-z-12 rotate-y-18 bg-sky-300/75 ...">2</div>  <div class="translate-x-12 rotate-y-90 bg-sky-300/75 ...">3</div>  <div class="-translate-x-12 -rotate-y-90 bg-sky-300/75 ...">4</div>  <div class="-translate-y-12 rotate-x-90 bg-sky-300/75 ...">5</div>  <div class="translate-y-12 -rotate-x-90 bg-sky-300/75 ...">6</div></div>
```

This is like moving a camera closer to or further away from an object.

### Removing a perspective

Use theperspective-noneutility to remove a perspective transform from an element:

```
<div class="perspective-none ...">  <!-- ... --></div>
```

### Using a custom value

Use theperspective-[<value>]syntaxto set theperspectivebased on a completely custom value:

```
<div class="perspective-[750px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theperspective-(<custom-property>)syntax:

```
<div class="perspective-(--my-perspective) ...">  <!-- ... --></div>
```

This is just a shorthand forperspective-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaperspectiveutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="perspective-midrange md:perspective-dramatic ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--perspective-*theme variables to customize theperspectiveutilities in your project:

```
@theme {  --perspective-remote: 1800px; }
```

Now theperspective-remoteutility can be used in your markup:

```
<div class="perspective-remote">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
