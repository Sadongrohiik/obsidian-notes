# https://tailwindcss.com/docs/caption-side

[Original link](https://tailwindcss.com/docs/caption-side)

## Examples

### Placing at top of table

Use thecaption-toputility to position a caption element at the top of a table:

```
<table>  <caption class="caption-top">    Table 3.1: Professional wrestlers and their signature moves.  </caption>  <thead>    <tr>      <th>Wrestler</th>      <th>Signature Move(s)</th>    </tr>  </thead>  <tbody>    <tr>      <td>"Stone Cold" Steve Austin</td>      <td>Stone Cold Stunner, Lou Thesz Press</td>    </tr>    <tr>      <td>Bret "The Hitman" Hart</td>      <td>The Sharpshooter</td>    </tr>    <tr>      <td>Razor Ramon</td>      <td>Razor's Edge, Fallaway Slam</td>    </tr>  </tbody></table>
```

### Placing at bottom of table

Use thecaption-bottomutility to position a caption element at the bottom of a table:

```
<table>  <caption class="caption-bottom">    Table 3.1: Professional wrestlers and their signature moves.  </caption>  <thead>    <tr>      <th>Wrestler</th>      <th>Signature Move(s)</th>    </tr>  </thead>  <tbody>    <tr>      <td>"Stone Cold" Steve Austin</td>      <td>Stone Cold Stunner, Lou Thesz Press</td>    </tr>    <tr>      <td>Bret "The Hitman" Hart</td>      <td>The Sharpshooter</td>    </tr>    <tr>      <td>Razor Ramon</td>      <td>Razor's Edge, Fallaway Slam</td>    </tr>  </tbody></table>
```

### Responsive design

Prefixacaption-sideutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<caption class="caption-top md:caption-bottom ...">  <!-- ... --></caption>
```

Learn more about using variants in thevariants documentation.
