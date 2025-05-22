# https://tailwindcss.com/docs/scroll-snap-stop

[Original link](https://tailwindcss.com/docs/scroll-snap-stop)

## Examples

### Forcing snap position stops

Use thesnap-alwaysutility together with thesnap-mandatoryutility to force a snap container to always stop on an element before the user can continue scrolling to the next item:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x snap-mandatory ...">  <div class="snap-center snap-always ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-center snap-always ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-center snap-always ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-center snap-always ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-center snap-always ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-center snap-always ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

### Skipping snap position stops

Use thesnap-normalutility to allow a snap container to skip past possible scroll snap positions:

Scroll in the grid of images to see the expected behavior

```
<div class="snap-x ...">  <div class="snap-center snap-normal ...">    <img src="/img/vacation-01.jpg" />  </div>  <div class="snap-center snap-normal ...">    <img src="/img/vacation-02.jpg" />  </div>  <div class="snap-center snap-normal ...">    <img src="/img/vacation-03.jpg" />  </div>  <div class="snap-center snap-normal ...">    <img src="/img/vacation-04.jpg" />  </div>  <div class="snap-center snap-normal ...">    <img src="/img/vacation-05.jpg" />  </div>  <div class="snap-center snap-normal ...">    <img src="/img/vacation-06.jpg" />  </div></div>
```

### Responsive design

Prefixascroll-snap-stoputilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="snap-always md:snap-normal ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
