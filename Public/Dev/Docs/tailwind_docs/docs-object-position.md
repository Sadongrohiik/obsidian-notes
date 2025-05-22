# https://tailwindcss.com/docs/object-position

[Original link](https://tailwindcss.com/docs/object-position)

## Examples

### Basic example

Use utilities likeobject-leftandobject-bottom-rightto specify how a replaced element's content should be positioned within its container:

Hover over examples to see the full image

object-top-left

object-top

object-top-right

object-left

object-center

object-right

object-bottom-left

object-bottom

object-bottom-right

```
<img class="size-24 object-top-left ..." src="/img/mountains.jpg" /><img class="size-24 object-top ..." src="/img/mountains.jpg" /><img class="size-24 object-top-right ..." src="/img/mountains.jpg" /><img class="size-24 object-left ..." src="/img/mountains.jpg" /><img class="size-24 object-center ..." src="/img/mountains.jpg" /><img class="size-24 object-right ..." src="/img/mountains.jpg" /><img class="size-24 object-bottom-left ..." src="/img/mountains.jpg" /><img class="size-24 object-bottom ..." src="/img/mountains.jpg" /><img class="size-24 object-bottom-right ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use theobject-[<value>]syntaxto set theobject positionbased on a completely custom value:

```
<img class="object-[25%_75%] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use theobject-(<custom-property>)syntax:

```
<img class="object-(--my-object) ..." src="/img/mountains.jpg" />
```

This is just a shorthand forobject-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixanobject-positionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="object-center md:object-top ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
