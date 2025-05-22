# https://tailwindcss.com/docs/scroll-snap-align

[Original link](https://tailwindcss.com/docs/scroll-snap-align)

## Examples

### Snapping to the center

Use thesnap-centerutility to snap an element to its center when being scrolled inside a snap container:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x ...">  <div class="snap-center ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-center ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

### Snapping to the start

Use thesnap-startutility to snap an element to its start when being scrolled inside a snap container:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x ...">  <div class="snap-start ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-start ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

### Snapping to the end

Use thesnap-endutility to snap an element to its end when being scrolled inside a snap container:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x ...">  <div class="snap-end ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-end ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-end ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-end ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-end ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-end ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

### Responsive design

Prefixascroll-snap-alignutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="snap-center md:snap-start ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
