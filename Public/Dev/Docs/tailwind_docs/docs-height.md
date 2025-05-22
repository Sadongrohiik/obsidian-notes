# https://tailwindcss.com/docs/height

[Original link](https://tailwindcss.com/docs/height)

## Examples

### Basic example

Useh-<number>utilities likeh-24andh-64to set an element to a fixed height based on the spacing scale:

```
<div class="h-96 ...">h-96</div><div class="h-80 ...">h-80</div><div class="h-64 ...">h-64</div><div class="h-48 ...">h-48</div><div class="h-40 ...">h-40</div><div class="h-32 ...">h-32</div><div class="h-24 ...">h-24</div>
```

### Using a percentage

Useh-fullorh-<fraction>utilities likeh-1/2andh-2/5to give an element a percentage-based height:

```
<div class="h-full ...">h-full</div><div class="h-9/10 ...">h-9/10</div><div class="h-3/4 ...">h-3/4</div><div class="h-1/2 ...">h-1/2</div><div class="h-1/3 ...">h-1/3</div>
```

### Matching viewport

Use theh-screenutility to make an element span the entire height of the viewport:

```
<div class="h-screen">  <!-- ... --></div>
```

### Matching dynamic viewport

Use theh-dvhutility to make an element span the entire height of the viewport, which changes as the browser UI expands or contracts:

Scroll the viewport to see the viewport height change

h-dvh

```
<div class="h-dvh">  <!-- ... --></div>
```

### Matching large viewport

Use theh-lvhutility to set an element's height to the largest possible height of the viewport:

Scroll the viewport to see the viewport height change

h-lvh

```
<div class="h-lvh">  <!-- ... --></div>
```

### Matching small viewport

Use theh-svhutility to set an element's height to the smallest possible height of the viewport:

Scroll the viewport to see the viewport height change

h-svh

```
<div class="h-svh">  <!-- ... --></div>
```

### Setting both width and height

Use utilities likesize-px,size-4, andsize-fullto set both the width and height of an element at the same time:

```
<div class="size-16 ...">size-16</div><div class="size-20 ...">size-20</div><div class="size-24 ...">size-24</div><div class="size-32 ...">size-32</div><div class="size-40 ...">size-40</div>
```

### Using a custom value

Use theh-[<value>]syntaxto set theheightbased on a completely custom value:

```
<div class="h-[32rem] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theh-(<custom-property>)syntax:

```
<div class="h-(--my-height) ...">  <!-- ... --></div>
```

This is just a shorthand forh-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaheightutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="h-1/2 md:h-full ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Theh-<number>andsize-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
