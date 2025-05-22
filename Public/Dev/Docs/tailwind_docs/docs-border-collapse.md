# https://tailwindcss.com/docs/border-collapse

[Original link](https://tailwindcss.com/docs/border-collapse)

## Examples

### Collapsing table borders

Use theborder-collapseutility to combine adjacent cell borders into a single border when possible:

```
<table class="border-collapse border border-gray-400 ...">  <thead>    <tr>      <th class="border border-gray-300 ...">State</th>      <th class="border border-gray-300 ...">City</th>    </tr>  </thead>  <tbody>    <tr>      <td class="border border-gray-300 ...">Indiana</td>      <td class="border border-gray-300 ...">Indianapolis</td>    </tr>    <tr>      <td class="border border-gray-300 ...">Ohio</td>      <td class="border border-gray-300 ...">Columbus</td>    </tr>    <tr>      <td class="border border-gray-300 ...">Michigan</td>      <td class="border border-gray-300 ...">Detroit</td>    </tr>  </tbody></table>
```

Note that this includes collapsing borders on the top-level<table>tag.

### Separating table borders

Use theborder-separateutility to force each cell to display its own separate borders:

```
<table class="border-separate border border-gray-400 ...">  <thead>    <tr>      <th class="border border-gray-300 ...">State</th>      <th class="border border-gray-300 ...">City</th>    </tr>  </thead>  <tbody>    <tr>      <td class="border border-gray-300 ...">Indiana</td>      <td class="border border-gray-300 ...">Indianapolis</td>    </tr>    <tr>      <td class="border border-gray-300 ...">Ohio</td>      <td class="border border-gray-300 ...">Columbus</td>    </tr>    <tr>      <td class="border border-gray-300 ...">Michigan</td>      <td class="border border-gray-300 ...">Detroit</td>    </tr>  </tbody></table>
```

### Responsive design

Prefixaborder-collapseutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<table class="border-collapse md:border-separate ...">  <!-- ... --></table>
```

Learn more about using variants in thevariants documentation.
