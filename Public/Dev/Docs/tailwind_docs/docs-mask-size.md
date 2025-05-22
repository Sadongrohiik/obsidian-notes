# https://tailwindcss.com/docs/mask-size

[Original link](https://tailwindcss.com/docs/mask-size)

## Examples

### Filling the container

Use themask-coverutility to scale the mask image until it fills the mask layer, cropping the image if needed:

```
<div class="mask-cover mask-[url(/img/scribble.png)] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Filling without cropping

Use themask-containutility to scale the mask image to the outer edges without cropping or stretching:

```
<div class="mask-contain mask-[url(/img/scribble.png)] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Using the default size

Use themask-autoutility to display the mask image at its default size:

```
<div class="mask-auto mask-[url(/img/scribble.png)] bg-[url(/img/mountains.jpg)] ..."></div>
```

### Using a custom value

Use themask-size-[<value>]syntaxto set themask image sizebased on a completely custom value:

```
<div class="mask-size-[auto_100px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use themask-size-(<custom-property>)syntax:

```
<div class="mask-size-(--my-mask-size) ...">  <!-- ... --></div>
```

This is just a shorthand formask-size-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixamask-sizeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="mask-auto md:mask-contain ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
