# https://tailwindcss.com/docs/background-image

[Original link](https://tailwindcss.com/docs/background-image)

## Examples

### Basic example

Use thebg-[<value>]syntax to set the background image of an element:

```
<div class="bg-[url(/img/mountains.jpg)] ..."></div>
```

### Adding a linear gradient

Use utilities likebg-linear-to-randbg-linear-<angle>with thecolor stop utilitiesto add a linear gradient to an element:

```
<div class="h-14 bg-linear-to-r from-cyan-500 to-blue-500"></div><div class="h-14 bg-linear-to-t from-sky-500 to-indigo-500"></div><div class="h-14 bg-linear-to-bl from-violet-500 to-fuchsia-500"></div><div class="h-14 bg-linear-65 from-purple-500 to-pink-500"></div>
```

### Adding a radial gradient

Use thebg-radialandbg-radial-[<position>]utilities with thecolor stop utilitiesto add a radial gradient to an element:

```
<div class="size-18 rounded-full bg-radial from-pink-400 from-40% to-fuchsia-700"></div><div class="size-18 rounded-full bg-radial-[at_50%_75%] from-sky-200 via-blue-400 to-indigo-900 to-90%"></div><div class="size-18 rounded-full bg-radial-[at_25%_25%] from-white to-zinc-900 to-75%"></div>
```

### Adding a conic gradient

Use thebg-conicandbg-conic-<angle>utilities with thecolor stop utilitiesto add a conic gradient to an element:

```
<div class="size-24 rounded-full bg-conic from-blue-600 to-sky-400 to-50%"></div><div class="size-24 rounded-full bg-conic-180 from-indigo-600 via-indigo-50 to-indigo-600"></div><div class="size-24 rounded-full bg-conic/decreasing from-violet-700 via-lime-300 to-violet-700"></div>
```

### Setting gradient color stops

Use utilities likefrom-indigo-500,via-purple-500, andto-pink-500to set the colors of the gradient stops:

```
<div class="bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 ..."></div>
```

### Setting gradient stop positions

Use utilities likefrom-10%,via-30%, andto-90%to set more precise positions for the gradient color stops:

```
<div class="bg-gradient-to-r from-indigo-500 from-10% via-sky-500 via-30% to-emerald-500 to-90% ..."></div>
```

### Changing interpolation mode

Use the interpolation modifier to control the interpolation mode of a gradient:

srgb

hsl

oklab

oklch

longer

shorter

increasing

decreasing

```
<div class="bg-linear-to-r/srgb from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/hsl from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/oklab from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/oklch from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/longer from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/shorter from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/increasing from-indigo-500 to-teal-400"></div><div class="bg-linear-to-r/decreasing from-indigo-500 to-teal-400"></div>
```

By default gradients are interpolated in theoklabcolor space.

### Removing background images

Use thebg-noneutility to remove an existing background image from an element:

```
<div class="bg-none"></div>
```

### Using a custom value

Use utilities likebg-linear-[<value>]andfrom-[<value>]to set thegradientbased on a completely custom value:

```
<div class="bg-linear-[25deg,red_5%,yellow_60%,lime_90%,teal] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebg-linear-(<custom-property>)syntax:

```
<div class="bg-linear-(--my-gradient) ...">  <!-- ... --></div>
```

This is just a shorthand forbg-linear-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackground-imageutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="from-purple-400 md:from-yellow-500 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now utilities likefrom-regal-blue,via-regal-blue,andto-regal-bluecan be used in your markup:

```
<div class="from-regal-blue">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
