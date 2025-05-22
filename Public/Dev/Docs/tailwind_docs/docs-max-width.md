# https://tailwindcss.com/docs/max-width

[Original link](https://tailwindcss.com/docs/max-width)

## Examples

### Basic example

Usemax-w-<number>utilities likemax-w-24andmax-w-64to set an element to a fixed maximum width based on the spacing scale:

Resize the example to see the expected behavior

```
<div class="w-full max-w-96 ...">max-w-96</div><div class="w-full max-w-80 ...">max-w-80</div><div class="w-full max-w-64 ...">max-w-64</div><div class="w-full max-w-48 ...">max-w-48</div><div class="w-full max-w-40 ...">max-w-40</div><div class="w-full max-w-32 ...">max-w-32</div><div class="w-full max-w-24 ...">max-w-24</div>
```

### Using a percentage

Usemax-w-fullormax-w-<fraction>utilities likemax-w-1/2andmax-w-2/5to give an element a percentage-based maximum width:

Resize the example to see the expected behavior

```
<div class="w-full max-w-9/10 ...">max-w-9/10</div><div class="w-full max-w-3/4 ...">max-w-3/4</div><div class="w-full max-w-1/2 ...">max-w-1/2</div><div class="w-full max-w-1/3 ...">max-w-1/3</div>
```

### Using the container scale

Use utilities likemax-w-smandmax-w-xlto set an element to a fixed maximum width based on the container scale:

Resize the example to see the expected behavior

```
<div class="max-w-md ...">  <!-- ... --></div>
```

### Using breakpoints container

Use thecontainerutility to set the maximum width of an element to match themin-widthof the current breakpoint. This is useful if you'd prefer to design for a fixed set of screen sizes instead of trying to accommodate a fully fluid viewport:

```
<div class="container">  <!-- ... --></div>
```

Note that unlike containers you might have used in other frameworks, Tailwind's container does not center itself automatically and does not have any built-in horizontal padding. Usemx-autoand thepx-<number>utilities to add these:

```
<div class="container mx-auto px-4">  <!-- ... --></div>
```

### Using a custom value

Use themax-w-[<value>]syntaxto set themaximum widthbased on a completely custom value:

```
<div class="max-w-[220px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themax-w-(<custom-property>)syntax:

```
<div class="max-w-(--my-max-width) ...">  <!-- ... --></div>
```

This is just a shorthand formax-w-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamax-widthutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="max-w-sm md:max-w-lg ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Themax-w-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
