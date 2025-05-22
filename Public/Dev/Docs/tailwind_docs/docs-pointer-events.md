# https://tailwindcss.com/docs/pointer-events

[Original link](https://tailwindcss.com/docs/pointer-events)

## Examples

### Ignoring pointer events

Use thepointer-events-noneutility to make an element ignore pointer events, like:hoverandclickevents:

Click the search icons to see the expected behavior

pointer-events-auto

pointer-events-none

```
<div class="relative ...">  <div class="pointer-events-auto absolute ...">    <svg class="absolute h-5 w-5 text-gray-400">      <!-- ... -->    </svg>  </div>  <input type="text" placeholder="Search" class="..." /></div><div class="relative ...">  <div class="pointer-events-none absolute ...">    <svg class="absolute h-5 w-5 text-gray-400">      <!-- ... -->    </svg>  </div>  <input type="text" placeholder="Search" class="..." /></div>
```

The pointer events will still trigger on child elements and pass-through to elements that are "beneath" the target.

### Restoring pointer events

Use thepointer-events-autoutility to revert to the default browser behavior for pointer events:

```
<div class="pointer-events-none md:pointer-events-auto ...">  <!-- ... --></div>
```
