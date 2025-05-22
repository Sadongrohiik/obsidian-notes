# https://tailwindcss.com/docs/position

[Original link](https://tailwindcss.com/docs/position)

## Examples

### Statically positioning elements

Use thestaticutility to position an element according to the normal flow of the document:

Static parent

Absolute child

```
<div class="static ...">  <p>Static parent</p>  <div class="absolute bottom-0 left-0 ...">    <p>Absolute child</p>  </div></div>
```

With statically positioned elements, anyoffsetswill be ignored and the element will not act as a position reference for absolutely positioned children.

### Relatively positioning elements

Use therelativeutility to position an element according to the normal flow of the document:

Relative parent

Absolute child

```
<div class="relative ...">  <p>Relative parent</p>  <div class="absolute bottom-0 left-0 ...">    <p>Absolute child</p>  </div></div>
```

With relatively position elements, anyoffsetsare calculated relative to the element's normal position and the element will act as a position reference for absolutely positioned children.

### Absolutely positioning elements

Use theabsoluteutility to position an elementoutsideof the normal flow of the document, causing neighboring elements to act as if the element doesn't exist:

With static positioning

Relative parent

Static parent

Static child?

Static sibling

With absolute positioning

Relative parent

Static parent

Absolute child

Static sibling

```
<div class="static ...">  <!-- Static parent -->  <div class="static ..."><p>Static child</p></div>  <div class="inline-block ..."><p>Static sibling</p></div>  <!-- Static parent -->  <div class="absolute ..."><p>Absolute child</p></div>  <div class="inline-block ..."><p>Static sibling</p></div></div>
```

With absolutely positioned elements, anyoffsetsare calculated relative to the nearest parent that has a position other thanstatic, and the element will act as a position reference for other absolutely positioned children.

### Fixed positioning elements

Use thefixedutility to position an element relative to the browser window:

Scroll this element to see the fixed positioning in action

```
<div class="relative">  <div class="fixed top-0 right-0 left-0">Contacts</div>  <div>    <div>      <img src="/img/andrew.jpg" />      <strong>Andrew Alfred</strong>    </div>    <div>      <img src="/img/debra.jpg" />      <strong>Debra Houston</strong>    </div>    <!-- ... -->  </div></div>
```

With fixed positioned elements, anyoffsetsare calculated relative to the viewport and the element will act as a position reference for absolutely positioned children:

### Sticky positioning elements

Use thestickyutility to position an element asrelativeuntil it crosses a specified threshold, then treat it asfixeduntil its parent is off screen:

Scroll this element to see the sticky positioning in action

```
<div>  <div>    <div class="sticky top-0 ...">A</div>    <div>      <div>        <img src="/img/andrew.jpg" />        <strong>Andrew Alfred</strong>      </div>      <div>        <img src="/img/aisha.jpg" />        <strong>Aisha Houston</strong>      </div>      <!-- ... -->    </div>  </div>  <div>    <div class="sticky top-0">B</div>    <div>      <div>        <img src="/img/bob.jpg" />        <strong>Bob Alfred</strong>      </div>      <!-- ... -->    </div>  </div>  <!-- ... --></div>
```

With sticky positioned elements, anyoffsetsare calculated relative to the element's normal position and the element will act as a position reference for absolutely positioned children.

### Responsive design

Prefixapositionutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="relative md:absolute ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
