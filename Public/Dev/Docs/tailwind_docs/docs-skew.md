# https://tailwindcss.com/docs/skew

[Original link](https://tailwindcss.com/docs/skew)

## Examples

### Basic example

Useskew-<number>utilities likeskew-4andskew-10to skew an element on both axes:

skew-3

skew-6

skew-12

```
<img class="skew-3 ..." src="/img/mountains.jpg" /><img class="skew-6 ..." src="/img/mountains.jpg" /><img class="skew-12 ..." src="/img/mountains.jpg" />
```

### Using negative values

Use-skew-<number>utilities like-skew-4and-skew-10to skew an element on both axes:

-skew-3

-skew-6

-skew-12

```
<img class="-skew-3 ..." src="/img/mountains.jpg" /><img class="-skew-6 ..." src="/img/mountains.jpg" /><img class="-skew-12 ..." src="/img/mountains.jpg" />
```

### Skewing on the x-axis

Useskew-x-<number>utilities likeskew-x-4and-skew-x-10to skew an element on the x-axis:

-skew-x-12

skew-x-6

skew-x-12

```
<img class="-skew-x-12 ..." src="/img/mountains.jpg" /><img class="skew-x-6 ..." src="/img/mountains.jpg" /><img class="skew-x-12 ..." src="/img/mountains.jpg" />
```

### Skewing on the y-axis

Useskew-y-<number>utilities likeskew-y-4and-skew-y-10to skew an element on the y-axis:

-skew-y-12

skew-y-6

skew-y-12

```
<img class="-skew-y-12 ..." src="/img/mountains.jpg" /><img class="skew-y-6 ..." src="/img/mountains.jpg" /><img class="skew-y-12 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use theskew-[<value>]syntaxto set theskewbased on a completely custom value:

```
<img class="skew-[3.142rad] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use theskew-(<custom-property>)syntax:

```
<img class="skew-(--my-skew) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forskew-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

PrefixskewX()andskewY()utilitieswith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="skew-3 md:skew-12 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
