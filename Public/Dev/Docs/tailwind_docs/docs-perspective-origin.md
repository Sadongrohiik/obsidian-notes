# https://tailwindcss.com/docs/perspective-origin

[Original link](https://tailwindcss.com/docs/perspective-origin)

## Examples

### Basic example

Use utilities likeperspective-origin-topandperspective-origin-bottom-leftto control where the vanishing point of a perspective is located:

perspective-origin-top-left

perspective-origin-bottom-right

```
<div class="size-20 perspective-near perspective-origin-top-left ...">  <div class="translate-z-12 rotate-x-0 bg-sky-300/75 ...">1</div>  <div class="-translate-z-12 rotate-y-18 bg-sky-300/75 ...">2</div>  <div class="translate-x-12 rotate-y-90 bg-sky-300/75 ...">3</div>  <div class="-translate-x-12 -rotate-y-90 bg-sky-300/75 ...">4</div>  <div class="-translate-y-12 rotate-x-90 bg-sky-300/75 ...">5</div>  <div class="translate-y-12 -rotate-x-90 bg-sky-300/75 ...">6</div></div><div class="size-20 perspective-near perspective-origin-bottom-right …">  <div class="translate-z-12 rotate-x-0 bg-sky-300/75 ...">1</div>  <div class="-translate-z-12 rotate-y-18 bg-sky-300/75 ...">2</div>  <div class="translate-x-12 rotate-y-90 bg-sky-300/75 ...">3</div>  <div class="-translate-x-12 -rotate-y-90 bg-sky-300/75 ...">4</div>  <div class="-translate-y-12 rotate-x-90 bg-sky-300/75 ...">5</div>  <div class="translate-y-12 -rotate-x-90 bg-sky-300/75 ...">6</div></div>
```

### Using a custom value

Use theperspective-origin-[<value>]syntaxto set theperspective originbased on a completely custom value:

```
<div class="perspective-origin-[200%_150%] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theperspective-origin-(<custom-property>)syntax:

```
<div class="perspective-origin-(--my-perspective-origin) ...">  <!-- ... --></div>
```

This is just a shorthand forperspective-origin-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaperspective-originutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="perspective-origin-center md:perspective-origin-bottom-left ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
