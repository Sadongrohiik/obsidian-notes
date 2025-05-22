# https://tailwindcss.com/docs/touch-action

[Original link](https://tailwindcss.com/docs/touch-action)

## Examples

### Basic example

Use utilities liketouch-pan-yandtouch-pinch-zoomto control how an element can be scrolled (panned) and zoomed (pinched) on touchscreens:

Try panning these images on a touchscreen

touch-auto

touch-none

touch-pan-x

touch-pan-y

```
<div class="h-48 w-full touch-auto overflow-auto ...">  <img class="h-auto w-[150%] max-w-none" src="..." /></div><div class="h-48 w-full touch-none overflow-auto ...">  <img class="h-auto w-[150%] max-w-none" src="..." /></div><div class="h-48 w-full touch-pan-x overflow-auto ...">  <img class="h-auto w-[150%] max-w-none" src="..." /></div><div class="h-48 w-full touch-pan-y overflow-auto ...">  <img class="h-auto w-[150%] max-w-none" src="..." /></div>
```

### Responsive design

Prefixatouch-actionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="touch-pan-x md:touch-auto ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
