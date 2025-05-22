# https://tailwindcss.com/docs/min-height

[Original link](https://tailwindcss.com/docs/min-height)

## Examples

### Basic example

Usemin-h-<number>utilities likemin-h-24andmin-h-64to set an element to a fixed minimum height based on the spacing scale:

```
<div class="h-20 ...">  <div class="min-h-80 ...">min-h-80</div>  <div class="min-h-64 ...">min-h-64</div>  <div class="min-h-48 ...">min-h-48</div>  <div class="min-h-40 ...">min-h-40</div>  <div class="min-h-32 ...">min-h-32</div>  <div class="min-h-24 ...">min-h-24</div></div>
```

### Using a percentage

Usemin-h-fullormin-h-<fraction>utilities likemin-h-1/2, andmin-h-2/5to give an element a percentage-based minimum height:

```
<div class="min-h-full ...">min-h-full</div><div class="min-h-9/10 ...">min-h-9/10</div><div class="min-h-3/4 ...">min-h-3/4</div><div class="min-h-1/2 ...">min-h-1/2</div><div class="min-h-1/3 ...">min-h-1/3</div>
```

### Using a custom value

Use themin-h-[<value>]syntaxto set theminimum heightbased on a completely custom value:

```
<div class="min-h-[220px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themin-h-(<custom-property>)syntax:

```
<div class="min-h-(--my-min-height) ...">  <!-- ... --></div>
```

This is just a shorthand formin-h-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamin-heightutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="h-24 min-h-0 md:min-h-full ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Themin-h-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
