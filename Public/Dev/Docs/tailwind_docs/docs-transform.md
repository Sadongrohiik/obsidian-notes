# https://tailwindcss.com/docs/transform

[Original link](https://tailwindcss.com/docs/transform)

## Examples

### Hardware acceleration

If your transition performs better when rendered by the GPU instead of the CPU, you can force hardware acceleration by adding thetransform-gpuutility:

```
<div class="scale-150 transform-gpu">  <!-- ... --></div>
```

Use thetransform-cpuutility to force things back to the CPU if you need to undo this conditionally.

### Removing transforms

Use thetransform-noneutility to remove all of the transforms on an element at once:

```
<div class="skew-y-3 md:transform-none">  <!-- ... --></div>
```

### Using a custom value

Use thetransform-[<value>]syntaxto set thetransformbased on a completely custom value:

```
<div class="transform-[matrix(1,2,3,4,5,6)] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thetransform-(<custom-property>)syntax:

```
<div class="transform-(--my-transform) ...">  <!-- ... --></div>
```

This is just a shorthand fortransform-[var(<custom-property>)]that adds thevar()function for you automatically.
