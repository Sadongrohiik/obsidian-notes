# https://tailwindcss.com/docs/background-size

[Original link](https://tailwindcss.com/docs/background-size)

## Examples

### Filling the container

Use thebg-coverutility to scale the background image until it fills the background layer, cropping the image if needed:

```
<div class="bg-[url(/img/mountains.jpg)] bg-cover bg-center"></div>
```

### Filling without cropping

Use thebg-containutility to scale the background image to the outer edges without cropping or stretching:

```
<div class="bg-[url(/img/mountains.jpg)] bg-contain bg-center"></div>
```

### Using the default size

Use thebg-autoutility to display the background image at its default size:

```
<div class="bg-[url(/img/mountains.jpg)] bg-auto bg-center bg-no-repeat"></div>
```

### Using a custom value

Use thebg-size-[<value>]syntaxto set thebackground sizebased on a completely custom value:

```
<div class="bg-size-[auto_100px] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thebg-size-(<custom-property>)syntax:

```
<div class="bg-size-(--my-image-size) ...">  <!-- ... --></div>
```

This is just a shorthand forbg-size-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixabackground-sizeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-auto md:bg-contain ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
