# https://tailwindcss.com/docs/box-sizing

[Original link](https://tailwindcss.com/docs/box-sizing)

## Examples

### Including borders and padding

Use thebox-borderutility to set an element'sbox-sizingtoborder-box, telling the browser to include the element's borders and padding when you give it a height or width.

This means a 100px × 100px element with a 2px border and 4px of padding on all sides will be rendered as 100px × 100px, with an internal content area of 88px × 88px:

```
<div class="box-border size-32 border-4 p-4 ...">  <!-- ... --></div>
```

Tailwind makes this the default for all elements in ourpreflight base styles.

### Excluding borders and padding

Use thebox-contentutility to set an element'sbox-sizingtocontent-box, telling the browser to add borders and padding on top of the element's specified width or height.

This means a 100px × 100px element with a 2px border and 4px of padding on all sides will actually be rendered as 112px × 112px, with an internal content area of 100px × 100px:

```
<div class="box-content size-32 border-4 p-4 ...">  <!-- ... --></div>
```

### Responsive design

Prefixabox-sizingutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="box-content md:box-border ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
