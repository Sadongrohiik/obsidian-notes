# https://tailwindcss.com/docs/overflow

[Original link](https://tailwindcss.com/docs/overflow)

## Examples

### Showing content that overflows

Use theoverflow-visibleutility to prevent content within an element from being clipped:

```
<div class="overflow-visible ...">  <!-- ... --></div>
```

Note that any content that overflows the bounds of the element will then be visible.

### Hiding content that overflows

Use theoverflow-hiddenutility to clip any content within an element that overflows the bounds of that element:

```
<div class="overflow-hidden ...">  <!-- ... --></div>
```

### Scrolling if needed

Use theoverflow-autoutility to add scrollbars to an element in the event that its content overflows the bounds of that element:

Scroll vertically

```
<div class="overflow-auto ...">  <!-- ... --></div>
```

Unlikeoverflow-scroll, which always shows scrollbars, this utility will only show them if scrolling is necessary.

### Scrolling horizontally if needed

Use theoverflow-x-autoutility to allow horizontal scrolling if needed:

Scroll horizontally

```
<div class="overflow-x-auto ...">  <!-- ... --></div>
```

### Scrolling vertically if needed

Use theoverflow-y-autoutility to allow vertical scrolling if needed:

Scroll vertically

```
<div class="h-32 overflow-y-auto ...">  <!-- ... --></div>
```

### Scrolling horizontally always

Use theoverflow-x-scrollutility to allow horizontal scrolling and always show scrollbars unless always-visible scrollbars are disabled by the operating system:

Scroll horizontally

```
<div class="overflow-x-scroll ...">  <!-- ... --></div>
```

### Scrolling vertically always

Use theoverflow-y-scrollutility to allow vertical scrolling and always show scrollbars unless always-visible scrollbars are disabled by the operating system:

Scroll vertically

```
<div class="overflow-y-scroll ...">  <!-- ... --></div>
```

### Scrolling in all directions

Use theoverflow-scrollutility to add scrollbars to an element:

Scroll vertically and horizontally

```
<div class="overflow-scroll ...">  <!-- ... --></div>
```

Unlikeoverflow-auto, which only shows scrollbars if they are necessary, this utility always shows them. Note that some operating systems (like macOS) hide unnecessary scrollbars regardless of this setting.

### Responsive design

Prefixanoverflowutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="overflow-auto md:overflow-scroll ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
