# https://tailwindcss.com/docs/object-fit

[Original link](https://tailwindcss.com/docs/object-fit)

## Examples

### Resizing to cover

Use theobject-coverutility to resize an element's content to cover its container:

```
<img class="h-48 w-96 object-cover ..." src="/img/mountains.jpg" />
```

### Containing within

Use theobject-containutility to resize an element's content to stay contained within its container:

```
<img class="h-48 w-96 object-contain ..." src="/img/mountains.jpg" />
```

### Stretching to fit

Use theobject-fillutility to stretch an element's content to fit its container:

```
<img class="h-48 w-96 object-fill ..." src="/img/mountains.jpg" />
```

### Scaling down

Use theobject-scale-downutility to display an element's content at its original size but scale it down to fit its container if necessary:

```
<img class="h-48 w-96 object-scale-down ..." src="/img/mountains.jpg" />
```

### Using the original size

Use theobject-noneutility to display an element's content at its original size ignoring the container size:

```
<img class="h-48 w-96 object-none ..." src="/img/mountains.jpg" />
```

### Responsive design

Prefixanobject-fitutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="object-contain md:object-cover" src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
