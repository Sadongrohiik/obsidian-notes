# https://tailwindcss.com/docs/line-height

[Original link](https://tailwindcss.com/docs/line-height)

## Examples

### Basic example

Use font size utilities liketext-sm/6andtext-lg/7to set the font size and line-height of an element at the same time:

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

```
<p class="text-base/6 ...">So I started to walk into the water...</p><p class="text-base/7 ...">So I started to walk into the water...</p><p class="text-base/8 ...">So I started to walk into the water...</p>
```

Each font size utility also sets a default line height when one isn't provided. You can learn more about these values and how to customize them in thefont-size documentation.

### Setting independently

Useleading-<number>utilities likeleading-6andleading-7to set the line height of an element independent of the font-size:

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

```
<p class="text-sm leading-6">So I started to walk into the water...</p><p class="text-sm leading-7">So I started to walk into the water...</p><p class="text-sm leading-8">So I started to walk into the water...</p>
```

### Removing the leading

Use theleading-noneutility to set the line height of an element equal to its font size:

The quick brown fox jumps over the lazy dog.

```
<p class="text-2xl leading-none ...">The quick brown fox...</p>
```

### Using a custom value

Use theleading-[<value>]syntaxto set theline heightbased on a completely custom value:

```
<p class="leading-[1.5] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use theleading-(<custom-property>)syntax:

```
<p class="leading-(--my-line-height) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forleading-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaline-heightutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="leading-5 md:leading-6 ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Theleading-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
