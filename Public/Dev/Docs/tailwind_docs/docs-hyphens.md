# https://tailwindcss.com/docs/hyphens

[Original link](https://tailwindcss.com/docs/hyphens)

## Examples

### Preventing hyphenation

Use thehyphens-noneutility to prevent words from being hyphenated even if the line break suggestion&shy;is used:

Officially recognized by the Duden dictionary as the longest word in German,Kraftfahrzeug­haftpflichtversicherungis a 36 letter word for motor vehicle liability insurance.

```
<p class="hyphens-none">  ... Kraftfahrzeug&shy;haftpflichtversicherung is a ...</p>
```

### Manual hyphenation

Use thehyphens-manualutility to only set hyphenation points where the line break suggestion&shy;is used:

Officially recognized by the Duden dictionary as the longest word in German,Kraftfahrzeug­haftpflichtversicherungis a 36 letter word for motor vehicle liability insurance.

```
<p class="hyphens-manual">  ... Kraftfahrzeug&shy;haftpflichtversicherung is a ...</p>
```

This is the default browser behavior.

### Automatic hyphenation

Use thehyphens-autoutility to allow the browser to automatically choose hyphenation points based on the language:

Officially recognized by the Duden dictionary as the longest word in German,Kraftfahrzeughaftpflichtversicherungis a 36 letter word for motor vehicle liability insurance.

```
<p class="hyphens-auto" lang="de">  ... Kraftfahrzeughaftpflichtversicherung is a ...</p>
```

The line break suggestion&shy;will be preferred over automatic hyphenation points.

### Responsive design

Prefixahyphensutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="hyphens-none md:hyphens-auto ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
