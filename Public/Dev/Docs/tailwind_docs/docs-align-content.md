# https://tailwindcss.com/docs/align-content

[Original link](https://tailwindcss.com/docs/align-content)

## Examples

### Start

Usecontent-startto pack rows in a container against the start of the cross axis:

```
<div class="grid h-56 grid-cols-3 content-start gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Center

Usecontent-centerto pack rows in a container in the center of the cross axis:

```
<div class="grid h-56 grid-cols-3 content-center gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### End

Usecontent-endto pack rows in a container against the end of the cross axis:

```
<div class="grid h-56 grid-cols-3 content-end gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Space between

Usecontent-betweento distribute rows in a container such that there is an equal amount of space between each line:

```
<div class="grid h-56 grid-cols-3 content-between gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Space around

Usecontent-aroundto distribute rows in a container such that there is an equal amount of space around each line:

```
<div class="grid h-56 grid-cols-3 content-around gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Space evenly

Usecontent-evenlyto distribute rows in a container such that there is an equal amount of space around each item, but also accounting for the doubling of space you would normally see between each item when usingcontent-around:

```
<div class="grid h-56 grid-cols-3 content-evenly gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Stretch

Usecontent-stretchto allow content items to fill the available space along the container’s cross axis:

```
<div class="grid h-56 grid-cols-3 content-stretch gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Normal

Usecontent-normalto pack content items in their default position as if noalign-contentvalue was set:

```
<div class="grid h-56 grid-cols-3 content-normal gap-4 ...">  <div>01</div>  <div>02</div>  <div>03</div>  <div>04</div>  <div>05</div></div>
```

### Responsive design

Prefixanalign-contentutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="grid content-start md:content-around ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
