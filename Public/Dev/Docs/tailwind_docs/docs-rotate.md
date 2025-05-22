# https://tailwindcss.com/docs/rotate

[Original link](https://tailwindcss.com/docs/rotate)

## Examples

### Basic example

Userotate-<number>utilities likerotate-45androtate-90to rotate an element by degrees:

rotate-45

rotate-90

rotate-210

```
<img class="rotate-45 ..." src="/img/mountains.jpg" /><img class="rotate-90 ..." src="/img/mountains.jpg" /><img class="rotate-210 ..." src="/img/mountains.jpg" />
```

### Using negative values

Use-rotate-<number>utilities like-rotate-45and-rotate-90to rotate an element counterclockwise by degrees:

-rotate-45

-rotate-90

-rotate-210

```
<img class="-rotate-45 ..." src="/img/mountains.jpg" /><img class="-rotate-90 ..." src="/img/mountains.jpg" /><img class="-rotate-210 ..." src="/img/mountains.jpg" />
```

### Rotating in 3D space

Userotate-x-<number>,rotate-y-<number>, androtate-z-<number>utilities likerotate-x-50,-rotate-y-30, androtate-z-45together to rotate an element in 3D space:

rotate-x-50

rotate-z-45

rotate-x-15

-rotate-y-30

rotate-y-25

rotate-z-30

```
<img class="rotate-x-50 rotate-z-45 ..." src="/img/mountains.jpg" /><img class="rotate-x-15 -rotate-y-30 ..." src="/img/mountains.jpg" /><img class="rotate-y-25 rotate-z-30 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use therotate-[<value>]syntaxto set therotationbased on a completely custom value:

```
<img class="rotate-[3.142rad] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use therotate-(<custom-property>)syntax:

```
<img class="rotate-(--my-rotation) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forrotate-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixarotateutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="rotate-45 md:rotate-60 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
