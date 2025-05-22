# https://tailwindcss.com/docs/display

[Original link](https://tailwindcss.com/docs/display)

## Examples

### Block and Inline

Use theinline,inline-block, andblockutilities to control the flow of text and elements:

```
<p>  When controlling the flow of text, using the CSS property <span class="inline">display: inline</span> will cause the  text inside the element to wrap normally.</p><p>  While using the property <span class="inline-block">display: inline-block</span> will wrap the element to prevent the  text inside from extending beyond its parent.</p><p>  Lastly, using the property <span class="block">display: block</span> will put the element on its own line and fill its  parent.</p>
```

### Flow Root

Use theflow-rootutility to create a block-level element with its ownblock formatting context:

```
<div class="p-4">  <div class="flow-root ...">    <div class="my-4 ...">Well, let me tell you something, ...</div>  </div>  <div class="flow-root ...">    <div class="my-4 ...">Sure, go ahead, laugh if you want...</div>  </div></div>
```

### Flex

Use theflexutility to create a block-level flex container:

```
<div class="flex items-center">  <img src="path/to/image.jpg" />  <div>    <strong>Andrew Alfred</strong>    <span>Technical advisor</span>  </div></div>
```

### Inline Flex

Use theinline-flexutility to create an inline flex container that flows with text:

Today I spent most of the day researching ways to take advantage of the fact that bottles can be returned for 10 cents in Michigan, but only 5 cents here.Kramerkeeps telling me there is no way to make it work, that he has run the numbers on every possible approach, but I just have to believe there's a way to make it work, there's simply too much opportunity here.

```
<p>  Today I spent most of the day researching ways to ...  <span class="inline-flex items-baseline">    <img src="/img/kramer.jpg" class="mx-1 size-5 self-center rounded-full" />    <span>Kramer</span>  </span>  keeps telling me there is no way to make it work, that ...</p>
```

### Grid

Use thegridutility to create a grid container:

```
<div class="grid grid-cols-3 grid-rows-3 gap-4">  <!-- ... --></div>
```

### Inline Grid

Use theinline-gridutility to create an inline grid container:

```
<span class="inline-grid grid-cols-3 gap-4">  <span>01</span>  <span>02</span>  <span>03</span>  <span>04</span>  <span>05</span>  <span>06</span></span><span class="inline-grid grid-cols-3 gap-4">  <span>01</span>  <span>02</span>  <span>03</span>  <span>04</span>  <span>05</span>  <span>06</span></span>
```

### Contents

Use thecontentsutility to create a "phantom" container whose children act like direct children of the parent:

```
<div class="flex ...">  <div class="flex-1 ...">01</div>  <div class="contents">    <div class="flex-1 ...">02</div>    <div class="flex-1 ...">03</div>  </div>  <div class="flex-1 ...">04</div></div>
```

### Table

Use thetable,table-row,table-cell,table-caption,table-column,table-column-group,table-header-group,table-row-group, andtable-footer-grouputilities to create elements that behave like their respective table elements:

```
<div class="table w-full ...">  <div class="table-header-group ...">    <div class="table-row">      <div class="table-cell text-left ...">Song</div>      <div class="table-cell text-left ...">Artist</div>      <div class="table-cell text-left ...">Year</div>    </div>  </div>  <div class="table-row-group">    <div class="table-row">      <div class="table-cell ...">The Sliding Mr. Bones (Next Stop, Pottersville)</div>      <div class="table-cell ...">Malcolm Lockyer</div>      <div class="table-cell ...">1961</div>    </div>    <div class="table-row">      <div class="table-cell ...">Witchy Woman</div>      <div class="table-cell ...">The Eagles</div>      <div class="table-cell ...">1972</div>    </div>    <div class="table-row">      <div class="table-cell ...">Shining Star</div>      <div class="table-cell ...">Earth, Wind, and Fire</div>      <div class="table-cell ...">1975</div>    </div>  </div></div>
```

### Hidden

Use thehiddenutility to remove an element from the document:

```
<div class="flex ...">  <div class="hidden ...">01</div>  <div>02</div>  <div>03</div></div>
```

To visually hide an element but keep it in the document, use thevisibilityproperty instead.

### Screen-reader only

Usesr-onlyto hide an element visually without hiding it from screen readers:

```
<a href="#">  <svg><!-- ... --></svg>  <span class="sr-only">Settings</span></a>
```

Usenot-sr-onlyto undosr-only, making an element visible to sighted users as well as screen readers:

```
<a href="#">  <svg><!-- ... --></svg>  <span class="sr-only sm:not-sr-only">Settings</span></a>
```

This can be useful when you want to visually hide something on small screens but show it on larger screens for example.

### Responsive design

Prefixadisplayutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<div class="flex md:inline-flex ...">  <!-- ... --></div>
```

Learn more about using variants in thevariants documentation.
