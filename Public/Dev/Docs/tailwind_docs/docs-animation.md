# https://tailwindcss.com/docs/animation

[Original link](https://tailwindcss.com/docs/animation)

## Examples

### Adding a spin animation

Use theanimate-spinutility to add a linear spin animation to elements like loading indicators:

```
<button type="button" class="bg-indigo-500 ..." disabled>  <svg class="mr-3 size-5 animate-spin ..." viewBox="0 0 24 24">    <!-- ... -->  </svg>  Processing…</button>
```

### Adding a ping animation

Use theanimate-pingutility to make an element scale and fade like a radar ping or ripple of water—useful for things like notification badges:

```
<span class="relative flex size-3">  <span class="absolute inline-flex h-full w-full animate-ping rounded-full bg-sky-400 opacity-75"></span>  <span class="relative inline-flex size-3 rounded-full bg-sky-500"></span></span>
```

### Adding a pulse animation

Use theanimate-pulseutility to make an element gently fade in and out—useful for things like skeleton loaders:

```
<div class="mx-auto w-full max-w-sm rounded-md border border-blue-300 p-4">  <div class="flex animate-pulse space-x-4">    <div class="size-10 rounded-full bg-gray-200"></div>    <div class="flex-1 space-y-6 py-1">      <div class="h-2 rounded bg-gray-200"></div>      <div class="space-y-3">        <div class="grid grid-cols-3 gap-4">          <div class="col-span-2 h-2 rounded bg-gray-200"></div>          <div class="col-span-1 h-2 rounded bg-gray-200"></div>        </div>        <div class="h-2 rounded bg-gray-200"></div>      </div>    </div>  </div></div>
```

### Adding a bounce animation

Use theanimate-bounceutility to make an element bounce up and down—useful for things like "scroll down" indicators:

```
<svg class="size-6 animate-bounce ...">  <!-- ... --></svg>
```

### Supporting reduced motion

For situations where the user has specified that they prefer reduced motion, you can conditionally apply animations and transitions using themotion-safeandmotion-reducevariants:

```
<button type="button" class="bg-indigo-600 ..." disabled>  <svg class="mr-3 size-5 motion-safe:animate-spin ..." viewBox="0 0 24 24">    <!-- ... -->  </svg>  Processing</button>
```

### Using a custom value

Use theanimate-[<value>]syntaxto set theanimationbased on a completely custom value:

```
<div class="animate-[wiggle_1s_ease-in-out_infinite] ...">  <!-- ... --></div>
```

For CSS variables, you can also use theanimate-(<custom-property>)syntax:

```
<div class="animate-(--my-animation) ...">  <!-- ... --></div>
```

This is just a shorthand foranimate-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixananimationutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="animate-none md:animate-spin ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--animate-*theme variables to customize theanimationutilities in your project:

```
@theme {  --animate-wiggle: wiggle 1s ease-in-out infinite;  @keyframes wiggle {    0%,    100% {      transform: rotate(-3deg);    }    50% {      transform: rotate(3deg);    }  }}
```

Now theanimate-wiggleutility can be used in your markup:

```
<div class="animate-wiggle">  <!-- ... --></div>
```

Learn more about customizing your theme in thetheme documentation.
