# https://tailwindcss.com/docs/scroll-snap-type

[Original link](https://tailwindcss.com/docs/scroll-snap-type)

## Examples

### Horizontal scroll snapping

Use thesnap-xutility to enable horizontal scroll snapping within an element:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x ...">  <div class="snap-center ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

For scroll snapping to work, you need to also set thescroll snap alignmenton the children.

### Mandatory scroll snapping

Use thesnap-mandatoryutility to force a snap container to always come to rest on a snap point:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x snap-mandatory ...">  <div class="snap-center ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

### Proximity scroll snapping

Use thesnap-proximityutility to make a snap container come to rest on snap points that are close in proximity:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x snap-proximity ...">  <div class="snap-center ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-05.jpg" />  </div></div>
```

### Responsive design

Prefixascroll-snap-typeutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="snap-none md:snap-x ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
