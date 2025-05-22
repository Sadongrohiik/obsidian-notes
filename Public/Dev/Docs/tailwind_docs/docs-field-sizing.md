# https://tailwindcss.com/docs/field-sizing

[Original link](https://tailwindcss.com/docs/field-sizing)

## Examples

### Sizing based on content

Use thefield-sizing-contentutility to allow a form control to adjust it's size based on the content:

Type in the input below to see the size change

```
<textarea class="field-sizing-content ..." rows="2">  Latex Salesman, Vanderlay Industries</textarea>
```

### Using a fixed size

Use thefield-sizing-fixedutility to make a form control use a fixed size:

Type in the input below to see the size remain the same

```
<textarea class="field-sizing-fixed w-80 ..." rows="2">  Latex Salesman, Vanderlay Industries</textarea>
```

### Responsive design

Prefixafield-sizingutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<input class="field-sizing-content md:field-sizing-fixed ..." />
```

Learn more about using variants in thevariants documentation.
