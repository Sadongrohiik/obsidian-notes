# https://tailwindcss.com/docs/transition-behavior

[Original link](https://tailwindcss.com/docs/transition-behavior)

## Examples

### Basic example

Use thetransition-discreteutility to start transitions when changing properties with a discrete set of values, such as elements that change fromhiddentoblock:

Interact with the checkboxes to see the expected behavior

```
<label class="peer ...">  <input type="checkbox" checked /></label><button class="hidden transition-all not-peer-has-checked:opacity-0 peer-has-checked:block ...">  I hide</button><label class="peer ...">  <input type="checkbox" checked /></label><button class="hidden transition-all transition-discrete not-peer-has-checked:opacity-0 peer-has-checked:block ...">  I fade out</button>
```

### Responsive design

Prefixatransition-behaviorutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<button class="transition-discrete md:transition-normal ...">  <!-- ... --></button>
```

Learn more about using variants in thevariants documentation.
