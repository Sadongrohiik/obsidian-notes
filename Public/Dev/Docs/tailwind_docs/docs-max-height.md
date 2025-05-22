# https://tailwindcss.com/docs/max-height

[Original link](https://tailwindcss.com/docs/max-height)

## Examples

### Basic example

Usemax-h-<number>utilities likemax-h-24andmax-h-64to set an element to a fixed maximum height based on the spacing scale:

```
<div class="h-96 ...">  <div class="h-full max-h-80 ...">max-h-80</div>  <div class="h-full max-h-64 ...">max-h-64</div>  <div class="h-full max-h-48 ...">max-h-48</div>  <div class="h-full max-h-40 ...">max-h-40</div>  <div class="h-full max-h-32 ...">max-h-32</div>  <div class="h-full max-h-24 ...">max-h-24</div></div>
```

### Using a percentage

Usemax-h-fullormax-h-<fraction>utilities likemax-h-1/2andmax-h-2/5to give an element a percentage-based maximum height:

```
<div class="h-96 ...">  <div class="h-full max-h-9/10 ...">max-h-9/10</div>  <div class="h-full max-h-3/4 ...">max-h-3/4</div>  <div class="h-full max-h-1/2 ...">max-h-1/2</div>  <div class="h-full max-h-1/4 ...">max-h-1/4</div>  <div class="h-full max-h-full ...">max-h-full</div></div>
```

### Using a custom value

Use themax-h-[<value>]syntaxto set themaximum heightbased on a completely custom value:

```
<div class="max-h-[220px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themax-h-(<custom-property>)syntax:

```
<div class="max-h-(--my-max-height) ...">  <!-- ... --></div>
```

This is just a shorthand formax-h-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamax-heightutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="h-48 max-h-full md:max-h-screen ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Themax-h-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
