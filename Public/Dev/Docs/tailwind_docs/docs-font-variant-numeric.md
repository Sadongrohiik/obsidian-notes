# https://tailwindcss.com/docs/font-variant-numeric

[Original link](https://tailwindcss.com/docs/font-variant-numeric)

## Examples

### Using ordinal glyphs

Use theordinalutility to enable special glyphs for the ordinal markers in fonts that support them:

1st

```
<p class="ordinal ...">1st</p>
```

### Using slashed zeroes

Use theslashed-zeroutility to force a zero with a slash in fonts that support them:

0

```
<p class="slashed-zero ...">0</p>
```

### Using lining figures

Use thelining-numsutility to use numeric glyphs that are aligned by their baseline in fonts that support them:

1234567890

```
<p class="lining-nums ...">1234567890</p>
```

### Using oldstyle figures

Use theoldstyle-numsutility to use numeric glyphs where some numbers have descenders in fonts that support them:

1234567890

```
<p class="oldstyle-nums ...">1234567890</p>
```

### Using proportional figures

Use theproportional-numsutility to use numeric glyphs that have proportional widths in fonts that support them:

12121

90909

```
<p class="proportional-nums ...">12121</p><p class="proportional-nums ...">90909</p>
```

### Using tabular figures

Use thetabular-numsutility to use numeric glyphs that have uniform/tabular widths in fonts that support them:

12121

90909

```
<p class="tabular-nums ...">12121</p><p class="tabular-nums ...">90909</p>
```

### Using diagonal fractions

Use thediagonal-fractionsutility to replace numbers separated by a slash with common diagonal fractions in fonts that support them:

1/2 3/4 5/6

```
<p class="diagonal-fractions ...">1/2 3/4 5/6</p>
```

### Using stacked fractions

Use thestacked-fractionsutility to replace numbers separated by a slash with common stacked fractions in fonts that support them:

1/2 3/4 5/6

```
<p class="stacked-fractions ...">1/2 3/4 5/6</p>
```

### Stacking multiple utilities

Thefont-variant-numericutilities are composable so you can enable multiple variants by combining them:

```
<dl class="...">  <dt class="...">Subtotal</dt>  <dd class="text-right slashed-zero tabular-nums ...">$100.00</dd>  <dt class="...">Tax</dt>  <dd class="text-right slashed-zero tabular-nums ...">$14.50</dd>  <dt class="...">Total</dt>  <dd class="text-right slashed-zero tabular-nums ...">$114.50</dd></dl>
```

### Resetting numeric font variants

Use thenormal-numsproperty to reset numeric font variants:

```
<p class="slashed-zero tabular-nums md:normal-nums ...">  <!-- ... --></p>
```

### Responsive design

Prefixafont-variant-numericutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="proportional-nums md:tabular-nums ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
