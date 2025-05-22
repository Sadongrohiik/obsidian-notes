# https://tailwindcss.com/docs/resize

[Original link](https://tailwindcss.com/docs/resize)

## Examples

### Resizing in all directions

Useresizeto make an element horizontally and vertically resizable:

Drag the textarea handle in the demo to see the expected behavior

```
<textarea class="resize rounded-md ..."></textarea>
```

### Resizing vertically

Useresize-yto make an element vertically resizable:

Drag the textarea handle in the demo to see the expected behavior

```
<textarea class="resize-y rounded-md ..."></textarea>
```

### Resizing horizontally

Useresize-xto make an element horizontally resizable:

Drag the textarea handle in the demo to see the expected behavior

```
<textarea class="resize-x rounded-md ..."></textarea>
```

### Prevent resizing

Useresize-noneto prevent an element from being resizable:

Notice that the textarea handle is gone

```
<textarea class="resize-none rounded-md"></textarea>
```

### Responsive design

Prefixaresizeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="resize-none md:resize ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
