# https://tailwindcss.com/docs/line-clamp

[Original link](https://tailwindcss.com/docs/line-clamp)

## Examples

### Basic example

Useline-clamp-<number>utilities likeline-clamp-2andline-clamp-3to truncate multi-line text after a specific number of lines:

Nulla dolor velit adipisicing duis excepteur esse in duis nostrud occaecat mollit incididunt deserunt sunt. Ut ut sunt laborum ex occaecat eu tempor labore enim adipisicing minim ad. Est in quis eu dolore occaecat excepteur fugiat dolore nisi aliqua fugiat enim ut cillum. Labore enim duis nostrud eu. Est ut eiusmod consequat irure quis deserunt ex. Enim laboris dolor magna pariatur. Dolor et ad sint voluptate sunt elit mollit officia ad enim sit consectetur enim.

```
<article>  <time>Mar 10, 2020</time>  <h2>Boost your conversion rate</h2>  <p class="line-clamp-3">    Nulla dolor velit adipisicing duis excepteur esse in duis nostrud occaecat mollit incididunt deserunt sunt. Ut ut    sunt laborum ex occaecat eu tempor labore enim adipisicing minim ad. Est in quis eu dolore occaecat excepteur fugiat    dolore nisi aliqua fugiat enim ut cillum. Labore enim duis nostrud eu. Est ut eiusmod consequat irure quis deserunt    ex. Enim laboris dolor magna pariatur. Dolor et ad sint voluptate sunt elit mollit officia ad enim sit consectetur    enim.  </p>  <div>    <img src="/img/lindsay.jpg" />    Lindsay Walton  </div></article>
```

### Undoing line clamping

Useline-clamp-noneto undo a previously applied line clamp utility:

```
<p class="line-clamp-3 lg:line-clamp-none">  <!-- ... --></p>
```

### Using a custom value

Use theline-clamp-[<value>]syntaxto set thenumber of linesbased on a completely custom value:

```
<p class="line-clamp-[calc(var(--characters)/100)] ...">  Lorem ipsum dolor sit amet...</p>
```

For CSS variables, you can also use theline-clamp-(<custom-property>)syntax:

```
<p class="line-clamp-(--my-line-count) ...">  Lorem ipsum dolor sit amet...</p>
```

This is just a shorthand forline-clamp-[var(<custom-property>)]that adds thevar()function for you automatically.

### Responsive design

Prefixaline-clamputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="line-clamp-3 md:line-clamp-4 ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
