# https://tailwindcss.com/docs/text-overflow

[Original link](https://tailwindcss.com/docs/text-overflow)

## Examples

### Truncating text

Use thetruncateutility to prevent text from wrapping and truncate overflowing text with an ellipsis (…) if needed:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="truncate">The longest word in any of the major...</p>
```

### Adding an ellipsis

Use thetext-ellipsisutility to truncate overflowing text with an ellipsis (…) if needed:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="overflow-hidden text-ellipsis">The longest word in any of the major...</p>
```

### Clipping text

Use thetext-cliputility to truncate the text at the limit of the content area:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="overflow-hidden text-clip">The longest word in any of the major...</p>
```

This is the default browser behavior.

### Responsive design

Prefixatext-overflowutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="text-ellipsis md:text-clip ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
