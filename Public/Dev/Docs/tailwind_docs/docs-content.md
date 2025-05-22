# https://tailwindcss.com/docs/content

[Original link](https://tailwindcss.com/docs/content)

## Examples

### Basic example

Use thecontent-[<value>]syntax, along with thebeforeandaftervariants, to set the contents of the::beforeand::afterpseudo-elements:

```
<p>Higher resolution means more than just a better-quality image. With aRetina 6K display, <a class="text-blue-600 after:content-['_↗']" href="...">Pro Display XDR</a> gives you nearly 40 percent more screen real estate thana 5K display.</p>
```

### Referencing an attribute value

Use thecontent-[attr(<name>)]syntax to reference a value stored in an attribute using theattr()CSS function:



```
<p before="Hello World" class="before:content-[attr(before)] ...">  <!-- ... --></p>
```

### Using spaces and underscores

Since whitespace denotes the end of a class in HTML, replace any spaces in an arbitrary value with an underscore:



```
<p class="before:content-['Hello_World'] ..."></p>
```

If you need to include an actual underscore, you can do this by escaping it with a backslash:



```
<p class="before:content-['Hello\_World']"></p>
```

### Using a CSS variable

Use thecontent-(<custom-property>)syntax to control the contents of the::beforeand::afterpseudo-elements using a CSS variable:

```
<p class="content-(--my-content)"></p>
```

This is just a shorthand forcontent-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixacontentutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="before:content-['Mobile'] md:before:content-['Desktop'] ..."></p>
```

Learn more about using variants in thevariants documentation.
