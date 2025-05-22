# https://tailwindcss.com/docs/text-wrap

[Original link](https://tailwindcss.com/docs/text-wrap)

## Examples

### Allowing text to wrap

Use thetext-wraputility to wrap overflowing text onto multiple lines at logical points in the text:

New Yorkers are facing the winter chill with less warmth this year as the city's most revered soup stand unexpectedly shutters, following a series of events that have left the community puzzled.

```
<article class="text-wrap">  <h3>Beloved Manhattan soup stand closes</h3>  <p>New Yorkers are facing the winter chill...</p></article>
```

### Preventing text from wrapping

Use thetext-nowraputility to prevent text from wrapping, allowing it to overflow if necessary:

New Yorkers are facing the winter chill with less warmth this year as the city's most revered soup stand unexpectedly shutters, following a series of events that have left the community puzzled.

```
<article class="text-nowrap">  <h3>Beloved Manhattan soup stand closes</h3>  <p>New Yorkers are facing the winter chill...</p></article>
```

### Balanced text wrapping

Use thetext-balanceutility to distribute the text evenly across each line:

New Yorkers are facing the winter chill with less warmth this year as the city's most revered soup stand unexpectedly shutters, following a series of events that have left the community puzzled.

```
<article>  <h3 class="text-balance">Beloved Manhattan soup stand closes</h3>  <p>New Yorkers are facing the winter chill...</p></article>
```

For performance reasons browsers limit text balancing to blocks that are ~6 lines or less, making it best suited for headings.

### Pretty text wrapping

Use thetext-prettyutility to prevent orphans (a single word on its own line) at the end of a text block:

New Yorkers are facing the winter chill with less warmth this year as the city's most revered soup stand unexpectedly shutters, following a series of events that have left the community puzzled.

```
<article>  <h3 class="text-pretty">Beloved Manhattan soup stand closes</h3>  <p>New Yorkers are facing the winter chill...</p></article>
```

### Responsive design

Prefixatext-wraputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<h1 class="text-pretty md:text-balance ...">  <!-- ... --></h1>
```

Learn more about using variants in thevariants documentation.
