# https://tailwindcss.com/docs/letter-spacing

[Original link](https://tailwindcss.com/docs/letter-spacing)

## Examples

### Basic example

Use utilities liketracking-tightandtracking-wideto set the letter spacing of an element:

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

```
<p class="tracking-tight ...">The quick brown fox ...</p><p class="tracking-normal ...">The quick brown fox ...</p><p class="tracking-wide ...">The quick brown fox ...</p>
```

### Using negative values

Using negative values doesn't make a ton of sense with the named letter spacing scale Tailwind includes out of the box, but if you've customized your scale to use numbers it can be useful:

```
@theme {  --tracking-1: 0em;  --tracking-2: 0.025em;  --tracking-3: 0.05em;  --tracking-4: 0.1em;}
```

To use a negative letter spacing value, prefix the class name with a dash to convert it to a negative value:

```
<p class="-tracking-2">The quick brown fox ...</p>
```

### Using a custom value

Use thetracking-[<value>]syntaxto set theletter spacingbased on a completely custom value:

```
<p class="tracking-[.25em] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use thetracking-(<custom-property>)syntax:

```
<p class="tracking-(--my-tracking) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand fortracking-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaletter-spacingutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="tracking-tight md:tracking-wide ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Use the--tracking-*theme variables to customize theletter spacingutilities in your project:

```
@theme {  --tracking-tightest: -0.075em; }
```

Now thetracking-tightestutility can be used in your markup:

```
<p class="tracking-tightest">  Lorem ipsum dolor sit amet...</p>
```

Learn more about customizing your theme in thetheme documentation.
