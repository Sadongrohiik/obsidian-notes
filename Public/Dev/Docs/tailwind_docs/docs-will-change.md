# https://tailwindcss.com/docs/will-change

[Original link](https://tailwindcss.com/docs/will-change)

## Examples

### Optimizing with will change

Use thewill-change-scroll,will-change-contentsandwill-change-transformutilities to optimize an element that's expected to change in the near future by instructing the browser to prepare the necessary animation before it actually begins:

```
<div class="overflow-auto will-change-scroll">  <!-- ... --></div>
```

It's recommended that you apply these utilities just before an element changes, and then remove it shortly after it finishes usingwill-change-auto.

Thewill-changeproperty is intended to be used as a last resort when dealing withknown performance problems. Avoid using these utilities too much, or simply in anticipation of performance issues, as it could actually cause the page to be less performant.

### Using a custom value

Use thewill-change-[<value>]syntaxto set thewill-changepropertybased on a completely custom value:

```
<div class="will-change-[top,left] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thewill-change-(<custom-property>)syntax:

```
<div class="will-change-(--my-properties) ...">  <!-- ... --></div>
```

This is just a shorthand forwill-change-[var(<custom-property>)]that adds thevar()function for you automatically.
