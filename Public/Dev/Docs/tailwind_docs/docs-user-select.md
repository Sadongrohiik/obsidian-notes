# https://tailwindcss.com/docs/user-select

[Original link](https://tailwindcss.com/docs/user-select)

## Examples

### Disabling text selection

Use theselect-noneutility to prevent selecting text in an element and its children:

Try selecting the text to see the expected behavior

```
<div class="select-none ...">The quick brown fox jumps over the lazy dog.</div>
```

### Allowing text selection

Use theselect-textutility to allow selecting text in an element and its children:

Try selecting the text to see the expected behavior

```
<div class="select-text ...">The quick brown fox jumps over the lazy dog.</div>
```

### Selecting all text in one click

Use theselect-allutility to automatically select all the text in an element when a user clicks:

Try clicking the text to see the expected behavior

```
<div class="select-all ...">The quick brown fox jumps over the lazy dog.</div>
```

### Using auto select behavior

Use theselect-autoutility to use the default browser behavior for selecting text:

Try selecting the text to see the expected behavior

```
<div class="select-auto ...">The quick brown fox jumps over the lazy dog.</div>
```

### Responsive design

Prefixanuser-selectutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="select-none md:select-all ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
