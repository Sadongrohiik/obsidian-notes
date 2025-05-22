# https://tailwindcss.com/docs/border-spacing

[Original link](https://tailwindcss.com/docs/border-spacing)

## Examples

### Basic example

Useborder-spacing-<number>utilities likeborder-spacing-2andborder-spacing-x-3to control the space between the borders of table cells withseparate borders:

```
<table class="border-separate border-spacing-2 border border-gray-400 dark:border-gray-500">  <thead>    <tr>      <th class="border border-gray-300 dark:border-gray-600">State</th>      <th class="border border-gray-300 dark:border-gray-600">City</th>    </tr>  </thead>  <tbody>    <tr>      <td class="border border-gray-300 dark:border-gray-700">Indiana</td>      <td class="border border-gray-300 dark:border-gray-700">Indianapolis</td>    </tr>    <tr>      <td class="border border-gray-300 dark:border-gray-700">Ohio</td>      <td class="border border-gray-300 dark:border-gray-700">Columbus</td>    </tr>    <tr>      <td class="border border-gray-300 dark:border-gray-700">Michigan</td>      <td class="border border-gray-300 dark:border-gray-700">Detroit</td>    </tr>  </tbody></table>
```

### Using a custom value

Use theborder-spacing-[<value>]syntaxto set theborder spacingbased on a completely custom value:

```
<table class="border-spacing-[7px] ...">  <!-- ... --></table>
```

For CSS variables, you can also use theborder-spacing-(<custom-property>)syntax:

```
<table class="border-spacing-(--my-border-spacing) ...">  <!-- ... --></table>
```

This is just a shorthand forborder-spacing-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaborder-spacingutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<table class="border-spacing-2 md:border-spacing-4 ...">  <!-- ... --></table>
```

Learn more about using variants in thevariants documentation.

## Customizing your theme

Theborder-spacing-<number>utilities are driven by the--spacingtheme variable, which can be customized in your own theme:

```
@theme {  --spacing: 1px; }
```

Learn more about customizing the spacing scale in thetheme variable documentation.
