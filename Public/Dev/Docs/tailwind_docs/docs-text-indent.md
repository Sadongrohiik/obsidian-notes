# https://tailwindcss.com/docs/text-indent

[Original link](https://tailwindcss.com/docs/text-indent)

## Examples

### Basic example

Useindent-<number>utilities likeindent-2andindent-8to set the amount of empty space (indentation) that's shown before text in a block:

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

```
<p class="indent-8">So I started to walk into the water...</p>
```

### Using negative values

To use a negative text indent value, prefix the class name with a dash to convert it to a negative value:

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

```
<p class="-indent-8">So I started to walk into the water...</p>
```

### Using a custom value

Use theindent-[<value>]syntaxto set thetext indentationbased on a completely custom value:

```
<p class="indent-[50%] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use theindent-(<custom-property>)syntax:

```
<p class="indent-(--my-indentation) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forindent-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixatext-indentutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="indent-4 md:indent-8 ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
