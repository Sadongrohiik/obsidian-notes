# https://tailwindcss.com/docs/gap

[Original link](https://tailwindcss.com/docs/gap)

## Examples

### Basic example

Usegap-<number>utilities likegap-2andgap-4to change the gap between both rows and columns in grid and flexbox layouts:

```
<div class="grid grid-cols-2 gap-4">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div></div>
```

### Changing row and column gaps independently

Usegap-x-<number>orgap-y-<number>utilities likegap-x-8andgap-y-4to change the gap between columns and rows independently:

```
<div class="grid grid-cols-3 gap-x-8 gap-y-4">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div>  <div>06</div></div>
```

### Using a custom value

Use utilities likegap-[<value>],gap-x-[<value>],andgap-y-[<value>]to set thegapbased on a completely custom value:

```
<div class="gap-[10vw] ...">  <!-- ... --></div>
```

For CSS variables, you can also use thegap-(<custom-property>)syntax:

```
<div class="gap-(--my-gap) ...">  <!-- ... --></div>
```

This is just a shorthand forgap-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixgap,column-gap,androw-gaputilitieswith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid gap-4 md:gap-6 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
