# https://tailwindcss.com/docs/mask-image

[Original link](https://tailwindcss.com/docs/mask-image)

## Examples

### Using an image mask

Use themask-[<value>]syntax to set the mask image of an element:

```
<div class="mask-[url(/img/scribble.png)] bg-[url(/img/mountains.jpg)] ...">  <!-- ... --></div>
```

### Masking edges

Use utilities likemask-b-from-<value>andmask-t-to-<value>to add a linear gradient mask to a single side of an element:

mask-t-from-50%

mask-r-from-30%

mask-l-from-50% mask-l-to-90%

mask-b-from-20% mask-b-to-80%

```
<div class="mask-t-from-50% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-r-from-30% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-l-from-50% mask-l-to-90% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-b-from-20% mask-b-to-80% bg-[url(/img/mountains.jpg)] ..."></div>
```

Additionally, use utilities likemask-x-from-70%andmask-y-to-90%to apply a mask to two sides of an element at the same time:

mask-x-from-70% mask-x-to-90%

mask-y-from-70% mask-y-to-90%

```
<div class="mask-x-from-70% mask-x-to-90% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-y-from-70% mask-y-to-90% bg-[url(/img/mountains.jpg)] ..."></div>
```

By default, linear gradient masks transition from black to transparent, but you can customize the gradient colors using themask-<side>-from-<color>andmask-<side>-to-<color>utilities.

### Adding an angled linear mask

Use utilities likemask-linear-<angle>,mask-linear-from-20, andmask-linear-to-40to add a custom linear gradient mask to an element:

mask-linear-50

-mask-linear-50

```
<div class="mask-linear-50 mask-linear-from-60% mask-linear-to-80% bg-[url(/img/mountains.jpg)] ..."></div><div class="-mask-linear-50 mask-linear-from-60% mask-linear-to-80% bg-[url(/img/mountains.jpg)] ..."></div>
```

### Adding a radial mask

Use themask-radial-from-<value>andmask-radial-to-<value>utilities to add a radial gradient mask to an element:

Speed

Built for power users

Work faster than ever with our keyboard shortcuts

```
<div class="flex items-center gap-4">  <img class="mask-radial-[100%_100%] mask-radial-from-75% mask-radial-at-left ..." src="/img/keyboard.png" />  <div class="font-medium">    <p class="font-mono text-xs text-blue-500 uppercase dark:text-blue-400">Speed</p>    <p class="mt-2 text-base text-gray-700 dark:text-gray-300">Built for power users</p>    <p class="mt-1 text-sm leading-relaxed text-balance text-gray-500">      Work faster than ever with customizable keyboard shortcuts    </p>  </div></div>
```

By default, radial gradient masks transition from black to transparent, but you can customize the gradient colors using themask-radial-from-<color>andmask-radial-to-<color>utilities.

#### Setting the radial position

Use utilities likemask-radial-at-bottom-leftandmask-radial-at-[35%_35%]to set the position of the center of the radial gradient mask:

mask-radial-at-top-left

mask-radial-at-top

mask-radial-at-top-right

mask-radial-at-left

mask-radial-at-center

mask-radial-at-right

mask-radial-at-bottom-left

mask-radial-at-bottom

mask-radial-at-bottom-right

```
<div class="mask-radial-at-top-left mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-top mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-top-right mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-left mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-center mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-right mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-bottom-left mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-bottom mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-at-bottom-right mask-radial-from-100% bg-[url(/img/mountains.jpg)] ..."></div>
```

This is different frommask-positionwhich sets the position of the mask image itself, not the radial gradient.

#### Setting the radial size

Use utilities likemask-radial-closest-cornerandmask-radial-farthest-sideto set the size of the radial gradient mask:

mask-radial-closest-side

mask-radial-closest-corner

mask-radial-farthest-side

mask-radial-farthest-corner

```
<div class="mask-radial-closest-side mask-radial-from-100% mask-radial-at-[30%_30%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-closest-corner mask-radial-from-100% mask-radial-at-[30%_30%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-farthest-side mask-radial-from-100% mask-radial-at-[30%_30%] bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-radial-farthest-corner mask-radial-from-100% mask-radial-at-[30%_30%] bg-[url(/img/mountains.jpg)] ..."></div>
```

When setting a custom radial gradient size, the units you can use depend on the<ending-shape>of the gradient which is set toellipseby default.

Withmask-circle, you can only use a single fixed length, likemask-radial-[5rem]. Whereas withmask-ellipse, you can specify each axis as a fixed length or percentage, likemask-radial-[40%_80%].

### Adding a conic mask

Use themask-conic-from-<value>,mask-conic-to-<value>andmask-conic-<angle>utilities to add a conic gradient mask to an element:

Storage used: 75%

0.48 GBout of 2 GB remaining

```
<div class="flex items-center gap-5 rounded-xl bg-white p-4 shadow-lg ring-1 ring-black/5 dark:bg-gray-800">  <div class="grid grid-cols-1 grid-rows-1">    <div class="border-4 border-gray-100 dark:border-gray-700 ..."></div>    <div class="border-4 border-amber-500 mask-conic-from-75% mask-conic-to-75% dark:border-amber-400 ..."></div>  </div>  <div class="w-0 flex-1 text-sm text-gray-950 dark:text-white">    <p class="font-medium">Storage used: 75%</p>    <p class="mt-1 text-gray-500 dark:text-gray-400"><span class="font-medium">0.48 GB</span> out of 2 GB remaining</p>  </div></div>
```

By default, conic gradient masks transition from black to transparent, but you can customize the gradient colors using themask-conic-from-<color>andmask-conic-to-<color>utilities.

### Combining masks

Gradient mask utilities, likemask-radial-from-<value>,mask-conic-to-<value>, andmask-l-from-<value>can be combined to create more complex gradient masks:

```
<div class="mask-b-from-50% mask-radial-[50%_90%] mask-radial-from-80% bg-[url(/img/mountains.jpg)] ..."></div><div class="mask-r-from-80% mask-b-from-80% mask-radial-from-70% mask-radial-to-85% bg-[url(/img/mountains.jpg)] ..."></div>
```

This behavior relies on the fact that Tailwind sets themask-compositepropertytointersectby default. Changing this property will affect how the gradient masks are combined.

### Removing mask images

Use themask-noneutility to remove an existing mask image from an element:

```
<div class="mask-none">  <!-- ... --></div>
```

### Using a custom value

Use utilities likemask-linear-[<value>]andmask-radial-[<value>]to set themask imagebased on a completely custom value:

```
<div class="mask-linear-[70deg,transparent_10%,black,transparent_80%] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themask-linear-(<custom-property>)syntax:

```
<div class="mask-linear-(--my-mask) ...">  <!-- ... --></div>
```

This is just a shorthand formask-linear-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamask-imageutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-radial-from-70% md:mask-radial-from-50% ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--color-*theme variables to customize thecolorutilities in your project:

```
@theme {  --color-regal-blue: #243c5a; }
```

Now utilities likemask-radial-from-regal-blue,mask-conic-to-regal-blue,andmask-b-from-regal-bluecan be used in your markup:

```
<div class="mask-radial-from-regal-blue">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
