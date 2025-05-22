# https://tailwindcss.com/docs/cursor

[Original link](https://tailwindcss.com/docs/cursor)

## Examples

### Basic example

Use utilities likecursor-pointerandcursor-grabto control which cursor is displayed when hovering over an element:

Hover over each button to see the cursor change

```
<button class="cursor-pointer ...">Submit</button><button class="cursor-progress ...">Saving...</button><button class="cursor-not-allowed ..." disabled>Confirm</button>
```

### Using a custom value

Use thecursor-[<value>]syntaxto set thecursorbased on a completely custom value:

```
<button class="cursor-[url(hand.cur),_pointer] ...">  <!-- ... --></button>
```

For CSS variables, you can also use thecursor-(<custom-property>)syntax:

```
<button class="cursor-(--my-cursor) ...">  <!-- ... --></button>
```

This is just a shorthand forcursor-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixacursorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="cursor-not-allowed md:cursor-auto ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.
