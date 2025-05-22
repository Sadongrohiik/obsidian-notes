# https://tailwindcss.com/docs/aspect-ratio

[Original link](https://tailwindcss.com/docs/aspect-ratio)

## Examples

### Basic example

Useaspect-<ratio>utilities likeaspect-3/2to give an element a specific aspect ratio:

Resize the example to see the expected behavior

```
<img class="aspect-3/2 object-cover ..." src="/img/villas.jpg" />
```

### Using a video aspect ratio

Use theaspect-videoutility to give a video element a 16 / 9 aspect ratio:

Resize the example to see the expected behavior

```
<iframe class="aspect-video ..." src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe>
```

### Using a custom value

Use theaspect-[<value>]syntaxto set theaspect ratiobased on a completely custom value:

```
<img class="aspect-[calc(4*3+1)/3] ..." src="/img/villas.jpg" />
```

For CSS variables, you can also use theaspect-(<custom-property>)syntax:

```
<img class="aspect-(--my-aspect-ratio) ..." src="/img/villas.jpg" />
```

This is just a shorthand foraspect-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanaspect-ratioutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<iframe class="aspect-video md:aspect-square ..." src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--aspect-*theme variables to customize theaspect ratioutilities in your project:

```
@theme {  --aspect-retro: 4 / 3; }
```

Now theaspect-retroutility can be used in your markup:

```
<iframe class="aspect-retro" src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe>
```

Learn more about customizing your theme in thetheme documentation.
