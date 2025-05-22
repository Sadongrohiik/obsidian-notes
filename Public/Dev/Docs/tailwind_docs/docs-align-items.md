# https://tailwindcss.com/docs/align-items

[Original link](https://tailwindcss.com/docs/align-items)

## Examples

### Stretch

Use theitems-stretchutility to stretch items to fill the container's cross axis:

```
<div class="flex items-stretch ...">  <div class="py-4">01</div>  <div class="py-12">02</div>  <div class="py-8">03</div></div>
```

### Start

Use theitems-startutility to align items to the start of the container's cross axis:

```
<div class="flex items-start ...">  <div class="py-4">01</div>  <div class="py-12">02</div>  <div class="py-8">03</div></div>
```

### Center

Use theitems-centerutility to align items along the center of the container's cross axis:

```
<div class="flex items-center ...">  <div class="py-4">01</div>  <div class="py-12">02</div>  <div class="py-8">03</div></div>
```

### End

Use theitems-endutility to align items to the end of the container's cross axis:

```
<div class="flex items-end ...">  <div class="py-4">01</div>  <div class="py-12">02</div>  <div class="py-8">03</div></div>
```

### Baseline

Use theitems-baselineutility to align items along the container's cross axis such that all of their baselines align:

```
<div class="flex items-baseline ...">  <div class="pt-2 pb-6">01</div>  <div class="pt-8 pb-12">02</div>  <div class="pt-12 pb-4">03</div></div>
```

### Last baseline

Use theitems-baseline-lastutility to align items along the container's cross axis such that all of their baselines align with the last baseline in the container:

Working on the future of astronaut recruitment at Space Recruit.

A multidisciplinary designer.

```
<div class="grid grid-cols-[1fr_auto] items-baseline-last">  <div>    <img src="img/spencer-sharp.jpg" />    <h4>Spencer Sharp</h4>    <p>Working on the future of astronaut recruitment at Space Recruit.</p>  </div>  <p>spacerecruit.com</p></div>
```

This is useful for ensuring that text items align with each other, even if they have different heights.

### Responsive design

Prefixanalign-itemsutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex items-stretch md:items-center ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
