# https://tailwindcss.com/docs/forced-color-adjust

[Original link](https://tailwindcss.com/docs/forced-color-adjust)

## Examples

### Opting out of forced colors

Use theforced-color-adjust-noneutility to opt an element out of the colors enforced by forced colors mode. This is useful in situations where enforcing a limited color palette will degrade usability.

Try emulating `forced-colors: active` in your developer tools to see the changes

Basic Tee

$35

```
<form>  <img src="/img/shirt.jpg" />  <div>    <h3>Basic Tee</h3>    <h3>$35</h3>    <fieldset>      <legend class="sr-only">Choose a color</legend>      <div class="forced-color-adjust-none ...">        <label>          <input class="sr-only" type="radio" name="color-choice" value="White" />          <span class="sr-only">White</span>          <span class="size-6 rounded-full border border-black/10 bg-white"></span>        </label>        <!-- ... -->      </div>    </fieldset>  </div></form>
```

You can also use theforced colors variantto conditionally add styles when the user has enabled a forced color mode.

### Restoring forced colors

Use theforced-color-adjust-autoutility to make an element adhere to colors enforced by forced colors mode:

```
<form>  <fieldset class="forced-color-adjust-none lg:forced-color-adjust-auto ...">    <legend>Choose a color:</legend>    <select class="hidden lg:block">      <option value="White">White</option>      <option value="Gray">Gray</option>      <option value="Black">Black</option>    </select>    <div class="lg:hidden">      <label>        <input class="sr-only" type="radio" name="color-choice" value="White" />        <!-- ... -->      </label>      <!-- ... -->    </div>  </fieldset></form>
```

This can be useful if you want to undo theforced-color-adjust-noneutility, for example on a larger screen size.

### Responsive design

Prefixaforced-color-adjustutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="forced-color-adjust-none md:forced-color-adjust-auto ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
