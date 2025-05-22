# https://tailwindcss.com/docs/white-space

[Original link](https://tailwindcss.com/docs/white-space)

## Examples

### Normal

Use thewhitespace-normalutility to cause text to wrap normally within an element. Newlines and spaces will be collapsed:

Hey everyone!

It’s almost 2022       and we still don’t know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.

You will never know.

```
<p class="whitespace-normal">Hey everyone!It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.You will never know.</p>
```

### No Wrap

Use thewhitespace-nowraputility to prevent text from wrapping within an element. Newlines and spaces will be collapsed:

Hey everyone!

It’s almost 2022       and we still don’t know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.

You will never know.

```
<p class="overflow-auto whitespace-nowrap">Hey everyone!It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.You will never know.</p>
```

### Pre

Use thewhitespace-preutility to preserve newlines and spaces within an element. Text will not be wrapped:

Hey everyone!

It’s almost 2022       and we still don’t know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.

You will never know.

```
<p class="overflow-auto whitespace-pre">Hey everyone!It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.You will never know.</p>
```

### Pre Line

Use thewhitespace-pre-lineutility to preserve newlines but not spaces within an element. Text will be wrapped normally:

Hey everyone!

It’s almost 2022       and we still don’t know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.

You will never know.

```
<p class="whitespace-pre-line">Hey everyone!It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.You will never know.</p>
```

### Pre Wrap

Use thewhitespace-pre-wraputility to preserve newlines and spaces within an element. Text will be wrapped normally:

Hey everyone!

It’s almost 2022       and we still don’t know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.

You will never know.

```
<p class="whitespace-pre-wrap">Hey everyone!It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.You will never know.</p>
```

### Break Spaces

Use thewhitespace-break-spacesutility to preserve newlines and spaces within an element. White space at the end of lines will not hang, but will wrap to the next line:

Hey everyone!

It’s almost 2022       and we still don’t know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.

You will never know.

```
<p class="whitespace-break-spaces">Hey everyone!It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.You will never know.</p>
```

### Responsive design

Prefixawhite-spaceutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="whitespace-pre md:whitespace-normal ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
