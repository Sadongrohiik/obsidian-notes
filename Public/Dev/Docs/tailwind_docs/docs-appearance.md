# https://tailwindcss.com/docs/appearance

[Original link](https://tailwindcss.com/docs/appearance)

## Examples

### Removing default appearance

Useappearance-noneto reset any browser specific styling on an element:

```
<select>  <option>Yes</option>  <option>No</option>  <option>Maybe</option></select><div class="grid">  <select class="col-start-1 row-start-1 appearance-none bg-gray-50 dark:bg-gray-800 ...">    <option>Yes</option>    <option>No</option>    <option>Maybe</option>  </select>  <svg class="pointer-events-none col-start-1 row-start-1 ...">    <!-- ... -->  </svg></div>
```

This utility is often used when creating custom form components.

### Restoring default appearance

Useappearance-autoto restore the default browser specific styling on an element:

Try emulating `forced-colors: active` in your developer tools to see the difference

```
<label>  <div>    <input type="checkbox" class="appearance-none forced-colors:appearance-auto ..." />    <svg class="invisible peer-checked:visible forced-colors:hidden ...">      <!-- ... -->    </svg>  </div>  Falls back to default appearance</label><label>  <div>    <input type="checkbox" class="appearance-none ..." />    <svg class="invisible peer-checked:visible ...">      <!-- ... -->    </svg>  </div>  Keeps custom appearance</label>
```

This is useful for reverting to the standard browser controls in certain accessibility modes.

### Responsive design

Prefixanappearanceutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<select class="appearance-auto md:appearance-none ...">  <!-- ... --></select>
```

Learn more about using variants in thevariants documentation.
