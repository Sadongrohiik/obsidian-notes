# https://tailwindcss.com/docs/table-layout

[Original link](https://tailwindcss.com/docs/table-layout)

## Examples

### Sizing columns automatically

Use thetable-autoutility to automatically size table columns to fit the contents of its cells:

```
<table class="table-auto">  <thead>    <tr>      <th>Song</th>      <th>Artist</th>      <th>Year</th>    </tr>  </thead>  <tbody>    <tr>      <td>The Sliding Mr. Bones (Next Stop, Pottersville)</td>      <td>Malcolm Lockyer</td>      <td>1961</td>    </tr>    <tr>      <td>Witchy Woman</td>      <td>The Eagles</td>      <td>1972</td>    </tr>    <tr>      <td>Shining Star</td>      <td>Earth, Wind, and Fire</td>      <td>1975</td>    </tr>  </tbody></table>
```

### Using fixed column widths

Use thetable-fixedutility to ignore the content of the table cells and use fixed widths for each column:

```
<table class="table-fixed">  <thead>    <tr>      <th>Song</th>      <th>Artist</th>      <th>Year</th>    </tr>  </thead>  <tbody>    <tr>      <td>The Sliding Mr. Bones (Next Stop, Pottersville)</td>      <td>Malcolm Lockyer</td>      <td>1961</td>    </tr>    <tr>      <td>Witchy Woman</td>      <td>The Eagles</td>      <td>1972</td>    </tr>    <tr>      <td>Shining Star</td>      <td>Earth, Wind, and Fire</td>      <td>1975</td>    </tr>  </tbody></table>
```

You can manually set the widths for some columns and the rest of the available width will be divided evenly amongst columns without an explicit width. The widths set in the first row will set the column width for the whole table.

### Responsive design

Prefixatable-layoututilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="table-auto md:table-fixed ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
