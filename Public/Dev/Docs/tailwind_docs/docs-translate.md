# https://tailwindcss.com/docs/translate

[Original link](https://tailwindcss.com/docs/translate)

## Examples

### Using the spacing scale

Usetranslate-<number>utilities liketranslate-2and-translate-4to translate an element on both axes based on the spacing scale:

-translate-6

translate-2

translate-8

```
<img class="-translate-6 ..." src="/img/mountains.jpg" /><img class="translate-2 ..." src="/img/mountains.jpg" /><img class="translate-8 ..." src="/img/mountains.jpg" />
```

### Using a percentage

Usetranslate-<fraction>utilities liketranslate-1/4and-translate-fullto translate an element on both axes by a percentage of the element's size:

-translate-1/4

translate-1/6

translate-1/2

```
<img class="-translate-1/4 ..." src="/img/mountains.jpg" /><img class="translate-1/6 ..." src="/img/mountains.jpg" /><img class="translate-1/2 ..." src="/img/mountains.jpg" />
```

### Translating on the x-axis

Usetranslate-x-<number>ortranslate-x-<fraction>utilities liketranslate-x-4andtranslate-x-1/4to translate an element on the x-axis:

-translate-x-4

translate-x-2

translate-x-1/2

```
<img class="-translate-x-4 ..." src="/img/mountains.jpg" /><img class="translate-x-2 ..." src="/img/mountains.jpg" /><img class="translate-x-1/2 ..." src="/img/mountains.jpg" />
```

### Translating on the y-axis

Usetranslate-y-<number>ortranslate-y-<fraction>utilities liketranslate-y-6andtranslate-y-1/3to translate an element on the y-axis:

-translate-y-4

translate-y-2

translate-y-1/2

```
<img class="-translate-y-4 ..." src="/img/mountains.jpg" /><img class="translate-y-2 ..." src="/img/mountains.jpg" /><img class="translate-y-1/2 ..." src="/img/mountains.jpg" />
```

### Translating on the z-axis

Usetranslate-z-<number>utilities liketranslate-z-6and-translate-z-12to translate an element on the z-axis:

-translate-z-8

translate-z-4

translate-z-12

```
<div class="transform-3d">  <img class="-translate-z-8 rotate-x-50 rotate-z-45 ..." src="/img/mountains.jpg" />  <img class="translate-z-2 rotate-x-50 rotate-z-45 ..." src="/img/mountains.jpg" />  <img class="translate-z-1/2 rotate-x-50 rotate-z-45 ..." src="/img/mountains.jpg" /></div>
```

Note that thetranslate-z-<number>utilities require thetransform-3dutility to be applied to the parent element.

### Using a custom value

Use thetranslate-[<value>]syntaxto set thetranslationbased on a completely custom value:

```
<img class="translate-[3.142rad] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use thetranslate-(<custom-property>)syntax:

```
<img class="translate-(--my-translate) ..." src="/img/mountains.jpg" />
```

This is just a shorthand fortranslate-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatranslateutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="translate-45 md:translate-60 ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
