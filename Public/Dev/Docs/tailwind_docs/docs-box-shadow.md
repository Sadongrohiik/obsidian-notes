# https://tailwindcss.com/docs/box-shadow

[Original link](https://tailwindcss.com/docs/box-shadow)

## Examples

### Basic example

Use utilities likeshadow-smandshadow-lgto apply different sized outer box shadows to an element:

shadow-md

shadow-lg

shadow-xl

```
<div class="shadow-md ..."></div><div class="shadow-lg ..."></div><div class="shadow-xl ..."></div>
```

### Changing the opacity

Use the opacity modifier to adjust the opacity of the box shadow:

shadow-xl

shadow-xl/20

shadow-xl/30

```
<div class="shadow-xl ..."></div><div class="shadow-xl/20 ..."></div><div class="shadow-xl/30 ..."></div>
```

The default box shadow opacities are quite low (25% or less), so increasing the opacity (to like 50%) will make the box shadows more pronounced.

### Setting the shadow color

Use utilities likeshadow-indigo-500andshadow-cyan-500/50to change the color of a box shadow:

shadow-cyan-500/50

shadow-blue-500/50

shadow-indigo-500/50

```
<button class="bg-cyan-500 shadow-lg shadow-cyan-500/50 ...">Subscribe</button><button class="bg-blue-500 shadow-lg shadow-blue-500/50 ...">Subscribe</button><button class="bg-indigo-500 shadow-lg shadow-indigo-500/50 ...">Subscribe</button>
```

By default colored shadows have an opacity of 100% but you can adjust this using the opacity modifier.

### Adding an inset shadow

Use utilities likeinset-shadow-xsandinset-shadow-smto apply an inset box shadow to an element:

inset-shadow-2xs

inset-shadow-xs

inset-shadow-sm

```
<div class="inset-shadow-2xs ..."></div><div class="inset-shadow-xs ..."></div><div class="inset-shadow-sm ..."></div>
```

You can adjust the opacity of an inset shadow using the opacity modifier, likeinset-shadow-sm/50. The default inset shadow opacities are quite low (5%), so increasing the opacity (to like 50%) will make the inset shadows more pronounced.

### Setting the inset shadow color

Use utilities likeinset-shadow-indigo-500andinset-shadow-cyan-500/50to change the color of an inset box shadow:

inset-shadow-indigo-500

inset-shadow-indigo-500/50

```
<div class="inset-shadow-sm inset-shadow-indigo-500 ..."></div><div class="inset-shadow-sm inset-shadow-indigo-500/50 ..."></div>
```

By default colored shadows have an opacity of 100% but you can adjust this using the opacity modifier.

### Adding a ring

Useringorring-<number>utilities likering-2andring-4to apply a solid box-shadow to an element:

ring

ring-2

ring-4

```
<button class="ring ...">Subscribe</button><button class="ring-2 ...">Subscribe</button><button class="ring-4 ...">Subscribe</button>
```

By default rings match thecurrentColorof the element they are applied to.

### Setting the ring color

Use utilities likering-indigo-500andring-cyan-500/50to change the color of a ring:

ring-blue-500

ring-blue-500/50

```
<button class="ring-2 ring-blue-500 ...">Subscribe</button><button class="ring-2 ring-blue-500/50 ...">Subscribe</button>
```

By default rings have an opacity of 100% but you can adjust this using the opacity modifier.

### Adding an inset ring

Useinset-ringorinset-ring-<number>utilities likeinset-ring-2andinset-ring-4to apply a solid inset box-shadow to an element:

inset-ring

inset-ring-2

inset-ring-4

```
<button class="inset-ring ...">Subscribe</button><button class="inset-ring-2 ...">Subscribe</button><button class="inset-ring-4 ...">Subscribe</button>
```

By default inset rings match thecurrentColorof the element they are applied to.

### Setting the inset ring color

Use utilities likeinset-ring-indigo-500andinset-ring-cyan-500/50to change the color of an inset ring:

inset-ring-blue-500

inset-ring-blue-500/50

```
<button class="inset-ring-2 inset-ring-blue-500 ...">Subscribe</button><button class="inset-ring-2 inset-ring-blue-500/50 ...">Subscribe</button>
```

By default inset rings have an opacity of 100% but you can adjust this using the opacity modifier.

### Removing a box shadow

Use theshadow-none,inset-shadow-none,ring-0, andinset-ring-0utilities to remove an existing box shadow from an element:

shadow-none

```
<div class="shadow-none ..."></div>
```

### Using a custom value

Use utilities likeshadow-[<value>],inset-shadow-[<value>],ring-[<value>],andinset-ring-[<value>]to set thebox shadowbased on a completely custom value:

```
<div class="shadow-[0_35px_35px_rgba(0,0,0,0.25)] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theshadow-(<custom-property>)syntax:

```
<div class="shadow-(--my-shadow) ...">  <!-- ... --></div>
```

This is just a shorthand forshadow-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabox-shadowutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="shadow-none md:shadow-lg ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

### Customizing shadows

Use the--shadow-*theme variables to customize thebox shadowutilities in your project:

```
@theme {  --shadow-3xl: 0 35px 35px rgba(0, 0, 0, 0.25); }
```

Now theshadow-3xlutility can be used in your markup:

```
<div class="shadow-3xl">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.

### Customizing inset shadows

Use the--inset-shadow-*theme variables to customize theinset box shadowutilities in your project:

```
@theme {  --inset-shadow-md: inset 0 2px 3px rgba(0, 0, 0, 0.25); }
```

Now theinset-shadow-mdutility can be used in your markup:

```
<div class="inset-shadow-md">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.

### Customizing shadow colors

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now utilities likeshadow-regal-blue,inset-shadow-regal-blue,ring-regal-blue,andinset-ring-regal-bluecan be used in your markup:

```
<div class="shadow-regal-blue">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
