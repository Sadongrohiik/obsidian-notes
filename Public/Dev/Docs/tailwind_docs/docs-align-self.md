# https://tailwindcss.com/docs/align-self

[Original link](https://tailwindcss.com/docs/align-self)

## Examples

### Auto

Use theself-autoutility to align an item based on the value of the container'salign-itemsproperty:

```
<div class="flex items-stretch ...">  <div>01</div>  <div class="self-auto ...">02</div>  <div>03</div></div>
```

### Start

Use theself-startutility to align an item to the start of the container's cross axis, despite the container'salign-itemsvalue:

```
<div class="flex items-stretch ...">  <div>01</div>  <div class="self-start ...">02</div>  <div>03</div></div>
```

### Center

Use theself-centerutility to align an item along the center of the container's cross axis, despite the container'salign-itemsvalue:

```
<div class="flex items-stretch ...">  <div>01</div>  <div class="self-center ...">02</div>  <div>03</div></div>
```

### End

Use theself-endutility to align an item to the end of the container's cross axis, despite the container'salign-itemsvalue:

```
<div class="flex items-stretch ...">  <div>01</div>  <div class="self-end ...">02</div>  <div>03</div></div>
```

### Stretch

Use theself-stretchutility to stretch an item to fill the container's cross axis, despite the container'salign-itemsvalue:

```
<div class="flex items-stretch ...">  <div>01</div>  <div class="self-stretch ...">02</div>  <div>03</div></div>
```

### Baseline

Use theself-baselineutility to align an item such that its baseline aligns with the baseline of the flex container's cross axis:

```
<div class="flex ...">  <div class="self-baseline pt-2 pb-6">01</div>  <div class="self-baseline pt-8 pb-12">02</div>  <div class="self-baseline pt-12 pb-4">03</div></div>
```

### Last baseline

Use theself-baseline-lastutility to align an item along the container's cross axis such that its baseline aligns with the last baseline in the container:

Working on the future of astronaut recruitment at Space Recruit.

A multidisciplinary designer.

```
<div class="grid grid-cols-[1fr_auto]">  <div>    <img src="img/spencer-sharp.jpg" />    <h4>Spencer Sharp</h4>    <p class="self-baseline-last">Working on the future of astronaut recruitment at Space Recruit.</p>  </div>  <p class="self-baseline-last">spacerecruit.com</p></div>
```

This is useful for ensuring that text items align with each other, even if they have different heights.

### Responsive design

Prefixanalign-selfutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="self-auto md:self-end ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
