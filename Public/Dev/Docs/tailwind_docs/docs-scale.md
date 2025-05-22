# https://tailwindcss.com/docs/scale

[Original link](https://tailwindcss.com/docs/scale)

## Examples

### Basic example

Usescale-<number>utilities likescale-75andscale-150to scale an element by a percentage of its original size:

scale-75

scale-100

scale-125

```
<img class="scale-75 ..." src="/img/mountains.jpg" /><img class="scale-100 ..." src="/img/mountains.jpg" /><img class="scale-125 ..." src="/img/mountains.jpg" />
```

### Scaling on the x-axis

Use thescale-x-<number>utilities likescale-x-75and-scale-x-150to scale an element on the x-axis by a percentage of its original width:

scale-x-75

scale-x-100

scale-x-125

```
<img class="scale-x-75 ..." src="/img/mountains.jpg" /><img class="scale-x-100 ..." src="/img/mountains.jpg" /><img class="scale-x-125 ..." src="/img/mountains.jpg" />
```

### Scaling on the y-axis

Use thescale-y-<number>utilities likescale-y-75and-scale-y-150to scale an element on the y-axis by a percentage of its original height:

scale-y-75

scale-y-100

scale-y-125

```
<img class="scale-y-75 ..." src="/img/mountains.jpg" /><img class="scale-y-100 ..." src="/img/mountains.jpg" /><img class="scale-y-125 ..." src="/img/mountains.jpg" />
```

### Using negative values

Use-scale-<number>,-scale-x-<number>or-scale-y-<number>utilities like-scale-x-75and-scale-125to mirror and scale down an element by a percentage of its original size:

-scale-x-75

-scale-100

-scale-y-125

```
<img class="-scale-x-75 ..." src="/img/mountains.jpg" /><img class="-scale-100 ..." src="/img/mountains.jpg" /><img class="-scale-y-125 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use thescale-[<value>]syntaxto set thescalebased on a completely custom value:

```
<img class="scale-[1.7] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thescale-(<custom-property>)syntax:

```
<img class="scale-(--my-scale) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forscale-[var(<custom-property>)]that adds thevar()function for you automatically.

### Applying on hover

Prefixascaleutility with a variant likehover:*to only apply the utility in that state:

```
<img class="scale-95 hover:scale-120 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
