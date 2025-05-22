# https://tailwindcss.com/docs/transform-origin

[Original link](https://tailwindcss.com/docs/transform-origin)

## Examples

### Basic example

Use utilities likeorigin-topandorigin-bottom-leftto set an element's transform origin:

origin-center

origin-top-left

origin-bottom

```
<img class="origin-center rotate-45 ..." src="/img/mountains.jpg" /><img class="origin-top-left rotate-12 ..." src="/img/mountains.jpg" /><img class="origin-bottom -rotate-12 ..." src="/img/mountains.jpg" />
```

### Using a custom value

Use theorigin-[<value>]syntaxto set thetransform originbased on a completely custom value:

```
<img class="origin-[33%_75%] ..." src="/img/mountains.jpg" />
```

For CSS variables, you can also use theorigin-(<custom-property>)syntax:

```
<img class="origin-(--my-transform-origin) ..." src="/img/mountains.jpg" />
```

This is just a shorthand fororigin-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatransform-originutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="origin-center md:origin-top ..." src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
