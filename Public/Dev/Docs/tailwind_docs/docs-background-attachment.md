# https://tailwindcss.com/docs/background-attachment

[Original link](https://tailwindcss.com/docs/background-attachment)

## Examples

### Fixing the background image

Use thebg-fixedutility to fix the background image relative to the viewport:

Scroll the content to see the background image fixed in place

Maybe we can live without libraries, people like you and me. Maybe. Sure, we're too old to change the world, but what about that kid, sitting down, opening a book, right now, in a branch at the local library and finding drawings of pee-pees and wee-wees on the Cat in the Hat and the Five Chinese Brothers? Doesn't HE deserve better?

Look. If you think this is about overdue fines and missing books, you'd better think again. This is about that kid's right to read a book without getting his mind warped! Or: maybe that turns you on, Seinfeld; maybe that's how y'get your kicks. You and your good-time buddies.

```
<div class="bg-[url(/img/mountains.jpg)] bg-fixed ...">  <!-- ... --></div>
```

### Scrolling with the container

Use thebg-localutility to scroll the background image with the container and the viewport:

Scroll the content to see the background image scroll with the container

Because the mail never stops. It just keeps coming and coming and coming, there's never a let-up. It's relentless. Every day it piles up more and more and more. And you gotta get it out but the more you get it out the more it keeps coming in. And then the barcode reader breaks and it's Publisher's Clearing House day.

```
<div class="bg-[url(/img/mountains.jpg)] bg-local ...">  <!-- ... --></div>
```

### Scrolling with the viewport

Use thebg-scrollutility to scroll the background image with the viewport, but not with the container:

Scroll the content to see the background image fixed in the container

Because the mail never stops. It just keeps coming and coming and coming, there's never a let-up. It's relentless. Every day it piles up more and more and more. And you gotta get it out but the more you get it out the more it keeps coming in. And then the barcode reader breaks and it's Publisher's Clearing House day.

```
<div class="bg-[url(/img/mountains.jpg)] bg-scroll ...">  <!-- ... --></div>
```

### Responsive design

Prefixabackground-attachmentutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="bg-local md:bg-fixed ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
