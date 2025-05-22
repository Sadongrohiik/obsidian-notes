# https://tailwindcss.com/docs/min-width

[Original link](https://tailwindcss.com/docs/min-width)

## Examples

### Basic example

Usemin-w-<number>utilities likemin-w-24andmin-w-64to set an element to a fixed minimum width based on the spacing scale:

```
<div class="w-20 ...">  <div class="min-w-80 ...">min-w-80</div>  <div class="min-w-64 ...">min-w-64</div>  <div class="min-w-48 ...">min-w-48</div>  <div class="min-w-40 ...">min-w-40</div>  <div class="min-w-32 ...">min-w-32</div>  <div class="min-w-24 ...">min-w-24</div></div>
```

### Using a percentage

Usemin-w-fullormin-w-<fraction>utilities likemin-w-1/2andmin-w-2/5to give an element a percentage-based minimum width:

```
<div class="flex ...">  <div class="min-w-3/4 ...">min-w-3/4</div>  <div class="w-full ...">w-full</div></div>
```

### Using the container scale

Use utilities likemin-w-smandmin-w-xlto set an element to a fixed minimum width based on the container scale:

```
<div class="w-40 ...">  <div class="min-w-lg ...">min-w-lg</div>  <div class="min-w-md ...">min-w-md</div>  <div class="min-w-sm ...">min-w-sm</div>  <div class="min-w-xs ...">min-w-xs</div>  <div class="min-w-2xs ...">min-w-2xs</div>  <div class="min-w-3xs ...">min-w-3xs</div></div>
```

### Using a custom value

Use themin-w-[<value>]syntaxto set theminimum widthbased on a completely custom value:

```
<div class="min-w-[220px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themin-w-(<custom-property>)syntax:

```
<div class="min-w-(--my-min-width) ...">  <!-- ... --></div>
```

This is just a shorthand formin-w-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamin-widthutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="w-24 min-w-full md:min-w-0 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Themin-w-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
