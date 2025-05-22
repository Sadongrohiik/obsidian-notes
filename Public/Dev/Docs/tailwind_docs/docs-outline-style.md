# https://tailwindcss.com/docs/outline-style

[Original link](https://tailwindcss.com/docs/outline-style)

## Examples

### Basic example

Use utilities likeoutline-solidandoutline-dashedto set the style of an element's outline:

outline-solid

outline-dashed

outline-dotted

outline-double

```
<button class="outline-2 outline-offset-2 outline-solid ...">Button A</button><button class="outline-2 outline-offset-2 outline-dashed ...">Button B</button><button class="outline-2 outline-offset-2 outline-dotted ...">Button C</button><button class="outline-3 outline-offset-2 outline-double ...">Button D</button>
```

### Hiding an outline

Use theoutline-hiddenutility to hide the default browser outline on focused elements, while still preserving the outline in forced colors mode:

Try emulating `forced-colors: active` in your developer tools to see the behavior

```
<input class="focus:border-indigo-600 focus:outline-hidden ..." type="text" />
```

It is highly recommended to apply your own focus styling for accessibility when using this utility.

### Removing outlines

Use theoutline-noneutility to completely remove the default browser outline on focused elements:

```
<div class="focus-within:outline-2 focus-within:outline-indigo-600 ...">  <textarea class="outline-none ..." placeholder="Leave a comment..." />  <button class="..." type="button">Post</button></div>
```

It is highly recommended to apply your own focus styling for accessibility when using this utility.

### Responsive design

Prefixanoutline-styleutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="outline md:outline-dashed ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
