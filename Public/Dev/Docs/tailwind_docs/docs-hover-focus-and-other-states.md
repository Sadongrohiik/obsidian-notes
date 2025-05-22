# https://tailwindcss.com/docs/hover-focus-and-other-states

[Original link](https://tailwindcss.com/docs/hover-focus-and-other-states)

Every utility class in Tailwind can be appliedconditionallyby adding a variant to the beginning of the class name that describes the condition you want to target.

For example, to apply thebg-sky-700class on hover, use thehover:bg-sky-700class:

Hover over this button to see the background color change

```
<button class="bg-sky-500 hover:bg-sky-700 ...">Save changes</button>
```

When writing CSS the traditional way, a single class name would do different things based on the current state:

Traditionally the same class name applies different styles on hover

```
.btn-primary {  background-color: #0ea5e9;}.btn-primary:hover {  background-color: #0369a1;}
```

In Tailwind, rather than adding the styles for a hover state to an existing class, you add another class to the element thatonlydoes something on hover:

In Tailwind, separate classes are used for the default state and the hover state

```
.bg-sky-500 {  background-color: #0ea5e9;}.hover\:bg-sky-700:hover {  background-color: #0369a1;}
```

Notice howhover:bg-sky-700onlydefines styles for the:hoverstate? It does nothing by default, but as soon as you hover over an element with that class, the background color will change tosky-700.

This is what we mean when we say a utility class can be appliedconditionally— by using variants you can control exactly how your design behaves in different states, without ever leaving your HTML.

Tailwind includes variants for just about everything you'll ever need, including:

These variants can even be stacked to target more specific situations, for example changing the background color in dark mode, at the medium breakpoint, on hover:

```
<button class="dark:md:hover:bg-fuchsia-600 ...">Save changes</button>
```

In this guide you'll learn about every variant available in the framework, how to use them with your own custom classes, and even how to create your own.

## Pseudo-classes

### :hover, :focus, and :active

Style elements on hover, focus, and active using thehover,focus, andactivevariants:

Try interacting with this button to see the hover, focus, and active states

```
<button class="bg-violet-500 hover:bg-violet-600 focus:outline-2 focus:outline-offset-2 focus:outline-violet-500 active:bg-violet-700 ...">  Save changes</button>
```

Tailwind also includes variants for other interactive states like:visited,:focus-within,:focus-visible, and more.

See thepseudo-class referencefor a complete list of available pseudo-class variants.

### :first, :last, :odd, and :even

Style an element when it is the first-child or last-child using thefirstandlastvariants:

Kristen Ramos

kristen.ramos@example.com

Floyd Miles

floyd.miles@example.com

Courtney Henry

courtney.henry@example.com

Ted Fox

ted.fox@example.com

```
<ul role="list">  {#each people as person}    <!-- Remove top/bottom padding when first/last child -->    <li class="flex py-4 first:pt-0 last:pb-0">      <img class="h-10 w-10 rounded-full" src={person.imageUrl} alt="" />      <div class="ml-3 overflow-hidden">        <p class="text-sm font-medium text-gray-900 dark:text-white">{person.name}</p>        <p class="truncate text-sm text-gray-500 dark:text-gray-400">{person.email}</p>      </div>    </li>  {/each}</ul>
```

You can also style an element when it's an odd or even child using theoddandevenvariants:

```
<table>  <!-- ... -->  <tbody>    {#each people as person}      <!-- Use different background colors for odd and even rows -->      <tr class="odd:bg-white even:bg-gray-50 dark:odd:bg-gray-900/50 dark:even:bg-gray-950">        <td>{person.name}</td>        <td>{person.title}</td>        <td>{person.email}</td>      </tr>    {/each}  </tbody></table>
```

Use thenth-*andnth-last-*variants to style children based on their position in the list:

```
<div class="nth-3:underline">  <!-- ... --></div><div class="nth-last-5:underline">  <!-- ... --></div><div class="nth-of-type-4:underline">  <!-- ... --></div><div class="nth-last-of-type-6:underline">  <!-- ... --></div>
```

You can pass any number you want to these by default, and use arbitrary values for more complex expressions likenth-[2n+1_of_li].

Tailwind also includes variants for other structural pseudo-classes like:only-child,:first-of-type,:empty, and more.

See thepseudo-class referencefor a complete list of available pseudo-class variants.

### :required and :disabled

Style form elements in different states using variants likerequired,invalid, anddisabled:

Try making the email address valid to see the styles change

```
<input  type="text"  value="tbone"  disabled  class="invalid:border-pink-500 invalid:text-pink-600 focus:border-sky-500 focus:outline focus:outline-sky-500 focus:invalid:border-pink-500 focus:invalid:outline-pink-500 disabled:border-gray-200 disabled:bg-gray-50 disabled:text-gray-500 disabled:shadow-none dark:disabled:border-gray-700 dark:disabled:bg-gray-800/20 ..."/>
```

Using variants for this sort of thing can reduce the amount of conditional logic in your templates, letting you use the same set of classes regardless of what state an input is in and letting the browser apply the right styles for you.

Tailwind also includes variants for other form states like:read-only,:indeterminate,:checked, and more.

See thepseudo-class referencefor a complete list of available pseudo-class variants.

### :has()

Use thehas-*variant to style an element based on the state or content of its descendants:

```
<label  class="has-checked:bg-indigo-50 has-checked:text-indigo-900 has-checked:ring-indigo-200 dark:has-checked:bg-indigo-950 dark:has-checked:text-indigo-200 dark:has-checked:ring-indigo-900 ...">  <svg fill="currentColor">    <!-- ... -->  </svg>  Google Pay  <input type="radio" class="checked:border-indigo-500 ..." /></label>
```

You can usehas-*with a pseudo-class, likehas-[:focus], to style an element based on the state of its descendants. You can also use element selectors, likehas-[img]orhas-[a], to style an element based on the content of its descendants.

#### Styling based on the descendants of a group

If you need to style an element based on the descendants of a parent element, you can mark the parent with thegroupclass and use thegroup-has-*variant to style the target element:

Product Designer atplaneteria.tech

Just happy to be here.

A multidisciplinary designer, working at the intersection of art and technology.alex-reed.com

Pushing pixels. Slinging divs.

```
<div class="group ...">  <img src="..." />  <h4>Spencer Sharp</h4>  <svg class="hidden group-has-[a]:block ..."><!-- ... --></svg>  <p>Product Designer at <a href="...">planeteria.tech</a></p></div>
```

#### Styling based on the descendants of a peer

If you need to style an element based on the descendants of a sibling element, you can mark the sibling with thepeerclass and use thepeer-has-*variant to style the target element:

```
<div>  <label class="peer ...">    <input type="checkbox" name="todo[1]" checked />    Create a to do list  </label>  <svg class="peer-has-checked:hidden ..."><!-- ... --></svg></div>
```

### :not()

Use thenot-variant to style an element when a condition is not true.

It's particularly powerful when combined with other pseudo-class variants, for example combiningnot-focus:withhover:to only apply hover styles when an element is not focused:

Try focusing on the button and then hovering over it

```
<button class="bg-indigo-600 hover:not-focus:bg-indigo-700">  <!-- ... --></button>
```

You can also combine thenot-variant with media query variants likeforced-colorsorsupportsto only style an element when something about the user's environment is not true:

```
<div class="not-supports-[display:grid]:flex">  <!-- ... --></div>
```

### Styling based on parent state

When you need to style an element based on the state of someparentelement, mark the parent with thegroupclass, and usegroup-*variants likegroup-hoverto style the target element:

Hover over the card to see both text elements change color

Create a new project from a variety of starting templates.

```
<a href="#" class="group ...">  <div>    <svg class="stroke-sky-500 group-hover:stroke-white ..." fill="none" viewBox="0 0 24 24">      <!-- ... -->    </svg>    <h3 class="text-gray-900 group-hover:text-white ...">New project</h3>  </div>  <p class="text-gray-500 group-hover:text-white ...">Create a new project from a variety of starting templates.</p></a>
```

This pattern works with every pseudo-class variant, for examplegroup-focus,group-active, or evengroup-odd.

#### Differentiating nested groups

When nesting groups, you can style something based on the state of aspecificparent group by giving that parent a unique group name using agroup/{name}class, and including that name in variants using classes likegroup-hover/{name}:

```
<ul role="list">  {#each people as person}    <li class="group/item ...">      <!-- ... -->      <a class="group/edit invisible group-hover/item:visible ..." href="tel:{person.phone}">        <span class="group-hover/edit:text-gray-700 ...">Call</span>        <svg class="group-hover/edit:translate-x-0.5 group-hover/edit:text-gray-500 ..."><!-- ... --></svg>      </a>    </li>  {/each}</ul>
```

Groups can be named however you like and don’t need to be configured in any way — just name your groups directly in your markup and Tailwind will automatically generate the necessary CSS.

#### Arbitrary groups

You can create one-offgroup-*variants on the fly by providing your own selector as anarbitrary valuebetween square brackets:

```
<div class="group is-published">  <div class="hidden group-[.is-published]:block">    Published  </div></div>
```

For more control, you can use the&character to mark where.groupshould end up in the final selector relative to the selector you are passing in:

```
<div class="group">  <div class="group-[:nth-of-type(3)_&]:block">    <!-- ... -->  </div></div>
```

#### Implicit groups

Thein-*variant works similarly togroupexcept you don't need to addgroupto the parent element:

```
<div tabindex="0" class="group">  <div class="opacity-50 group-focus:opacity-100"><div tabindex="0">  <div class="opacity-50 in-focus:opacity-100">    <!-- ... -->  </div></div>
```

Thein-*variant responds to state changes in any parent, so if you want more fine-grained control you'll need to usegroupinstead.

### Styling based on sibling state

When you need to style an element based on the state of asiblingelement, mark the sibling with thepeerclass, and usepeer-*variants likepeer-invalidto style the target element:

Try making the email address valid to see the warning disappear

Please provide a valid email address.

```
<form>  <label class="block">    <span class="...">Email</span>    <input type="email" class="peer ..." />    <p class="invisible peer-invalid:visible ...">Please provide a valid email address.</p>  </label></form>
```

This makes it possible to do all sorts of neat tricks, likefloating labelsfor example without any JS.

This pattern works with every pseudo-class variant, for examplepeer-focus,peer-required, andpeer-disabled.

It's important to note that thepeermarker can only be used onprevioussiblings because of how thesubsequent-sibling combinatorworks in CSS:

Won't work, only previous siblings can be marked as peers

```
<label>  <span class="peer-invalid:text-red-500 ...">Email</span>  <input type="email" class="peer ..." /></label>
```

#### Differentiating peers

When using multiple peers, you can style something on the state of aspecificpeer by giving that peer a unique name using apeer/{name}class, and including that name in variants using classes likepeer-checked/{name}:

```
<fieldset>  <legend>Published status</legend>  <input id="draft" class="peer/draft" type="radio" name="status" checked />  <label for="draft" class="peer-checked/draft:text-sky-500">Draft</label>  <input id="published" class="peer/published" type="radio" name="status" />  <label for="published" class="peer-checked/published:text-sky-500">Published</label>  <div class="hidden peer-checked/draft:block">Drafts are only visible to administrators.</div>  <div class="hidden peer-checked/published:block">Your post will be publicly visible on your site.</div></fieldset>
```

Peers can be named however you like and don’t need to be configured in any way — just name your peers directly in your markup and Tailwind will automatically generate the necessary CSS.

#### Arbitrary peers

You can create one-offpeer-*variants on the fly by providing your own selector as anarbitrary valuebetween square brackets:

```
<form>  <label for="email">Email:</label>  <input id="email" name="email" type="email" class="is-dirty peer" required />  <div class="peer-[.is-dirty]:peer-required:block hidden">This field is required.</div>  <!-- ... --></form>
```

For more control, you can use the&character to mark where.peershould end up in the final selector relative to the selector you are passing in:

```
<div>  <input type="text" class="peer" />  <div class="hidden peer-[:nth-of-type(3)_&]:block">    <!-- ... -->  </div></div>
```

## Pseudo-elements

### ::before and ::after

Style the::beforeand::afterpseudo-elements using thebeforeandaftervariants:

```
<label>  <span class="text-gray-700 after:ml-0.5 after:text-red-500 after:content-['*'] ...">Email</span>  <input type="email" name="email" class="..." placeholder="you@example.com" /></label>
```

When using these variants, Tailwind will automatically addcontent: ''by default so you don't have to specify it unless you want a different value:

```
<blockquote class="text-center text-2xl font-semibold text-gray-900 italic dark:text-white">  When you look  <span class="relative inline-block before:absolute before:-inset-1 before:block before:-skew-y-3 before:bg-pink-500">    <span class="relative text-white dark:text-gray-950">annoyed</span>  </span>  all the time, people think that you're busy.</blockquote>
```

It's worth noting that you don't really need::beforeand::afterpseudo-elements for most things in Tailwind projects — it's usually simpler to just use a real HTML element.

For example, here's the same design from above but using a<span>instead of the::beforepseudo-element, which is a little easier to read and is actually less code:

```
<blockquote class="text-center text-2xl font-semibold text-gray-900 italic">  When you look  <span class="relative">    <span class="absolute -inset-1 block -skew-y-3 bg-pink-500" aria-hidden="true"></span>    <span class="relative text-white">annoyed</span>  </span>  all the time, people think that you're busy.</blockquote>
```

Savebeforeandafterfor situations where it's important that the content of the pseudo-element is not actually in the DOM and can't be selected by the user.

### ::placeholder

Style the placeholder text of any input or textarea using theplaceholdervariant:

```
<input  class="placeholder:text-gray-500 placeholder:italic ..."  placeholder="Search for anything..."  type="text"  name="search"/>
```

### ::file

Style the button in file inputs using thefilevariant:

```
<input  type="file"  class="file:mr-4 file:rounded-full file:border-0 file:bg-violet-50 file:px-4 file:py-2 file:text-sm file:font-semibold file:text-violet-700 hover:file:bg-violet-100 dark:file:bg-violet-600 dark:file:text-violet-100 dark:hover:file:bg-violet-500 ..."/>
```

### ::marker

Style the counters or bullets in lists using themarkervariant:

## Ingredients

```
<ul role="list" class="list-disc marker:text-sky-400 ...">  <li>5 cups chopped Porcini mushrooms</li>  <li>1/2 cup of olive oil</li>  <li>3lb of celery</li></ul>
```

We've designed themarkervariant to be inheritable, so although you can use it directly on an<li>element, you can also use it on a parent to avoid repeating yourself.

### ::selection

Style the active text selection using theselectionvariant:

Try selecting some of this text with your mouse

So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all living things but I tell you Jerry at that moment, Iwasa marine biologist.

```
<div class="selection:bg-fuchsia-300 selection:text-fuchsia-900">  <p>    So I started to walk into the water. I won't lie to you boys, I was terrified. But I pressed on, and as I made my    way past the breakers a strange calm came over me. I don't know if it was divine intervention or the kinship of all    living things but I tell you Jerry at that moment, I <em>was</em> a marine biologist.  </p></div>
```

We've designed theselectionvariant to be inheritable, so you can add it anywhere in the tree and it will be applied to all descendant elements.

This makes it easy to set the selection color to match your brand across your entire site:

```
<html>  <head>    <!-- ... -->  </head>  <body class="selection:bg-pink-300">    <!-- ... -->  </body></html>
```

### ::first-line and ::first-letter

Style the first line in a block of content using thefirst-linevariant, and the first letter using thefirst-lettervariant:

Well, let me tell you something, funny boy. Y'know that little stamp, the one that says "New York Public Library"? Well that may not mean anything to you, but that means a lot to me. One whole hell of a lot.

Sure, go ahead, laugh if you want to. I've seen your type before: Flashy, making the scene, flaunting convention. Yeah, I know what you're thinking. What's this guy making such a big stink about old library books? Well, let me give you a hint, junior.

```
<div class="text-gray-700">  <p    class="first-letter:float-left first-letter:mr-3 first-letter:text-7xl first-letter:font-bold first-letter:text-gray-900 first-line:tracking-widest first-line:uppercase"  >    Well, let me tell you something, funny boy. Y'know that little stamp, the one that says "New York Public Library"?  </p>  <p class="mt-6">Well that may not mean anything to you, but that means a lot to me. One whole hell of a lot.</p></div>
```

### ::backdrop

Style the backdrop of anative<dialog>elementusing thebackdropvariant:

```
<dialog class="backdrop:bg-gray-50">  <form method="dialog">    <!-- ... -->  </form></dialog>
```

If you're using native<dialog>elements in your project, you may also want to read aboutstyling open/closed statesusing theopenvariant.

## Media and feature queries

### Responsive breakpoints

To style an element at a specific breakpoint, use responsive variants likemdandlg.

For example, this will render a 3-column grid on mobile, a 4-column grid on medium-width screens, and a 6-column grid on large-width screens:

```
<div class="grid grid-cols-3 md:grid-cols-4 lg:grid-cols-6">  <!-- ... --></div>
```

To style an element based on the width of a parent element instead of the viewport, use variants like@mdand@lg:

```
<div class="@container">  <div class="flex flex-col @md:flex-row">    <!-- ... -->  </div></div>
```

Check out theResponsive designdocumentation for an in-depth look at how these features work.

### prefers-color-scheme

Theprefers-color-schememedia query tells you whether the user prefers a light theme or dark theme, and is usually configured at the operating system level.

Use utilities with no variant to target light mode, and use thedarkvariant to provide overrides for dark mode:

Light mode

The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.

Dark mode

The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.

```
<div class="bg-white dark:bg-gray-900 ...">  <!-- ... -->  <h3 class="text-gray-900 dark:text-white ...">Writes upside-down</h3>  <p class="text-gray-500 dark:text-gray-400 ...">    The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.  </p></div>
```

Check out theDark Modedocumentation for an in-depth look at how this feature works.

### prefers-reduced-motion

Theprefers-reduced-motionmedia query tells you if the user has requested that you minimize non-essential motion.

Use themotion-reducevariant to conditionally add styles when the user has requested reduced motion:

Try emulating `prefers-reduced-motion: reduce` in your developer tools to hide the spinner

```
<button type="button" class="bg-indigo-500 ..." disabled>  <svg class="animate-spin motion-reduce:hidden ..." viewBox="0 0 24 24"><!-- ... --></svg>  Processing...</button>
```

Tailwind also includes amotion-safevariant that only adds styles when the user hasnotrequested reduced motion. This can be useful when using themotion-reducehelper would mean having to "undo" a lot of styles:

```
<!-- Using `motion-reduce` can mean lots of "undoing" styles --><button class="transition hover:-translate-y-0.5 motion-reduce:transition-none motion-reduce:hover:translate-y-0 ...">  Save changes</button><!-- Using `motion-safe` is less code in these situations --><button class="motion-safe:transition motion-safe:hover:-translate-x-0.5 ...">Save changes</button>
```

### prefers-contrast

Theprefers-contrastmedia query tells you if the user has requested more or less contrast.

Use thecontrast-morevariant to conditionally add styles when the user has requested more contrast:

Try emulating `prefers-contrast: more` in your developer tools to see the changes

We need this to steal your identity.

```
<label class="block">  <span class="block text-sm font-medium text-gray-700">Social Security Number</span>  <input    class="border-gray-200 placeholder-gray-400 contrast-more:border-gray-400 contrast-more:placeholder-gray-500 ..."  />  <p class="text-gray-600 opacity-10 contrast-more:opacity-100 ...">We need this to steal your identity.</p></label>
```

Tailwind also includes acontrast-lessvariant you can use to conditionally add styles when the user has requested less contrast.

### forced-colors

Theforced-colorsmedia query indicates if the user is using a forced colors mode. These modes override your site's colors with a user defined palette for text, backgrounds, links and buttons.

Use theforced-colorsvariant to conditionally add styles when the user has enabled a forced color mode:

Try emulating `forced-colors: active` in your developer tools to see the changes

Cyan

Blue

Indigo

Purple

```
<label>  <input type="radio" class="appearance-none forced-colors:appearance-auto" />  <p class="hidden forced-colors:block">Cyan</p>  <div class="bg-cyan-200 forced-colors:hidden ..."></div>  <div class="bg-cyan-500 forced-colors:hidden ..."></div></label>
```

Use thenot-forced-colorsvariant to apply styles based when the user isnotusing a forced colors mode:

```
<div class="not-forced-colors:appearance-none ...">  <!-- ... --></div>
```

Tailwind also includes aforced color adjustutilities to opt in and out of forced colors.

### inverted-colors

Use theinverted-colorsvariant to conditionally add styles when the user has enabled an inverted color scheme:

```
<div class="shadow-xl inverted-colors:shadow-none ...">  <!-- ... --></div>
```

### pointer and any-pointer

Thepointermedia query tells you whether the user has a primary pointing device, like a mouse, and the accuracy of that pointing device.

Use thepointer-finevariant to target an accurate pointing device, like a mouse or trackpad, or thepointer-coarsevariant to target a less accurate pointing device, like a touchscreen, which can be useful for providing larger click targets on touch devices:

Try emulating a touch device in your developer tools to see the changes

```
<fieldset aria-label="Choose a memory option">  <div class="flex items-center justify-between">    <div>RAM</div>    <a href="#"> See performance specs </a>  </div>  <div class="mt-4 grid grid-cols-6 gap-2 pointer-coarse:mt-6 pointer-coarse:grid-cols-3 pointer-coarse:gap-4">    <label class="p-2 pointer-coarse:p-4 ...">      <input type="radio" name="memory-option" value="4 GB" className="sr-only" />      <span>4 GB</span>    </label>    <!-- ... -->  </div></fieldset>
```

Whilepointeronly targets the primary pointing device,any-pointeris used to target any of the pointing devices that might be available. Use theany-pointer-fineandany-pointer-coarsevariants to provide different styles if at least one connected pointing device meets the criteria.

You can usepointer-noneandany-pointer-noneto target the absence of a pointing device.

### orientation

Use theportraitandlandscapevariants to conditionally add styles when the viewport is in a specific orientation:

```
<div>  <div class="portrait:hidden">    <!-- ... -->  </div>  <div class="landscape:hidden">    <p>This experience is designed to be viewed in landscape. Please rotate your device to view the site.</p>  </div></div>
```

### scripting

Use thenoscriptvariant to conditionally add styles based on whether the user has scripting, such as JavaScript, enabled:

```
<div class="hidden noscript:block">  <p>This experience requires JavaScript to function. Please enable JavaScript in your browser settings.</p></div>
```

### print

Use theprintvariant to conditionally add styles that only apply when the document is being printed:

```
<div>  <article class="print:hidden">    <h1>My Secret Pizza Recipe</h1>    <p>This recipe is a secret, and must not be shared with anyone</p>    <!-- ... -->  </article>  <div class="hidden print:block">Are you seriously trying to print this? It's secret!</div></div>
```

### @supports

Use thesupports-[...]variant to style things based on whether a certain feature is supported in the user's browser:

```
<div class="flex supports-[display:grid]:grid ...">  <!-- ... --></div>
```

Under the hood thesupports-[...]variant generates@supports rulesand takes anything you’d use with@supports (...)between the square brackets, like a property/value pair, and even expressions usingandandor.

For terseness, if you only need to check if a property is supported (and not a specific value), you can just specify the property name:

```
<div class="bg-black/75 supports-backdrop-filter:bg-black/25 supports-backdrop-filter:backdrop-blur ...">  <!-- ... --></div>
```

Use thenot-supports-[...]variant to style things based on whether a certain feature is not supported in the user's browser:

```
<div class="not-supports-[display:grid]:flex">  <!-- ... --></div>
```

You can configure shortcuts for common@supportsrules you're using in your project by creating a new variant in thesupports-*namespace:

```
@custom-variant supports-grid {  @supports (display: grid) {    @slot;  }}
```

You can then use these customsupports-*variants in your project:

```
<div class="supports-grid:grid">  <!-- ... --></div>
```

### @starting-style

Use thestartingvariant to set the appearance of an element when it is first rendered in the DOM, or transitions fromdisplay: noneto visible:

```
<div>  <button popovertarget="my-popover">Check for updates</button>  <div popover id="my-popover" class="opacity-0 starting:open:opacity-0 ...">    <!-- ... -->  </div></div>
```

## Attribute selectors

### ARIA states

Use thearia-*variant to conditionally style things based onARIA attributes.

For example, to apply thebg-sky-700class when thearia-checkedattribute is set totrue, use thearia-checked:bg-sky-700class:

```
<div aria-checked="true" class="bg-gray-600 aria-checked:bg-sky-700">  <!-- ... --></div>
```

By default we've included variants for the most common boolean ARIA attributes:

You can customize whicharia-*variants are available by creating a new variant:

```
@custom-variant aria-asc (&[aria-sort="ascending"]);@custom-variant aria-desc (&[aria-sort="descending"]);
```

If you need to use a one-offariavariant that doesn’t make sense to include in your project, or for more complex ARIA attributes that take specific values, use square brackets to generate a property on the fly using any arbitrary value:

```
<table>  <thead>    <tr>      <th        aria-sort="ascending"        class="aria-[sort=ascending]:bg-[url('/img/down-arrow.svg')] aria-[sort=descending]:bg-[url('/img/up-arrow.svg')]"      >        Invoice #      </th>      <!-- ... -->    </tr>  </thead>  <!-- ... --></table>
```

ARIA state variants can also target parent and sibling elements using thegroup-aria-*andpeer-aria-*variants:

```
<table>  <thead>    <tr>    <th aria-sort="ascending" class="group">      Invoice #      <svg class="group-aria-[sort=ascending]:rotate-0 group-aria-[sort=descending]:rotate-180"><!-- ... --></svg>    </th>    <!-- ... -->    </tr>  </thead>  <!-- ... --></table>
```

### Data attributes

Use thedata-*variant to conditionally apply styles based ondata attributes.

To check if a data attribute exists (and not a specific value), you can just specify the attribute name:

```
<!-- Will apply --><div data-active class="border border-gray-300 data-active:border-purple-500">  <!-- ... --></div><!-- Will not apply --><div class="border border-gray-300 data-active:border-purple-500">  <!-- ... --></div>
```

If you need to check for a specific value you may use an arbitrary value:

```
<!-- Will apply --><div data-size="large" class="data-[size=large]:p-8">  <!-- ... --></div><!-- Will not apply --><div data-size="medium" class="data-[size=large]:p-8">  <!-- ... --></div>
```

Alternatively, you can configure shortcuts for common data attributes you're using in your project by creating a new variant in thedata-*namespace:

```
@import "tailwindcss";@custom-variant data-checked (&[data-ui~="checked"]);
```

You can then use these customdata-*variants in your project:

```
<div data-ui="checked active" class="data-checked:underline">  <!-- ... --></div>
```

### RTL support

Use thertlandltrvariants to conditionally add styles in right-to-left and left-to-right modes respectively when building multi-directional layouts:

Left-to-right

Tom Cook

Director of Operations

Right-to-left

تامر كرم

الرئيس التنفيذي

```
<div class="group flex items-center">  <img class="h-12 w-12 shrink-0 rounded-full" src="..." alt="" />  <div class="ltr:ml-3 rtl:mr-3">    <p class="text-gray-700 group-hover:text-gray-900 ...">...</p>    <p class="text-gray-500 group-hover:text-gray-700 ...">...</p>  </div></div>
```

Remember, these variants are only useful if you are building a site that needs to supportbothleft-to-right and right-to-left layouts. If you're building a site that only needs to support a single direction, you don't need these variants — just apply the styles that make sense for your content.

### Open/closed state

Use theopenvariant to conditionally add styles when a<details>or<dialog>element is in an open state:

Try toggling the disclosure to see the styles change

The mug is round. The jar is round. They should call it Roundtine.

```
<details class="border border-transparent open:border-black/10 open:bg-gray-100 ..." open>  <summary class="text-sm leading-6 font-semibold text-gray-900 select-none">Why do they call it Ovaltine?</summary>  <div class="mt-3 text-sm leading-6 text-gray-600">    <p>The mug is round. The jar is round. They should call it Roundtine.</p>  </div></details>
```

This variant also targets the:popover-openpseudo-class for popovers:

```
<div>  <button popovertarget="my-popover">Open Popover</button>  <div popover id="my-popover" class="opacity-0 open:opacity-100 ...">    <!-- ... -->  </div></div>
```

### Styling inert elements

Theinertvariant lets you style elements marked with theinertattribute:

Get notified when someones posts a comment on a post.

Get notified when someones mentions you.

```
<form>  <legend>Notification preferences</legend>  <fieldset>    <input type="radio" />    <label> Custom </label>    <fieldset inert class="inert:opacity-50">      <!-- ... -->    </fieldset>    <input type="radio" />    <label> Everything </label>  </fieldset></form>
```

This is useful for adding visual cues that make it clear that sections of content aren't interactive.

## Child selectors

### Styling direct children

While it's generally preferable to put utility classes directly on child elements, you can use the*variant in situations where you need to style direct children that you don’t have control over:

## Categories

```
<div>  <h2>Categories<h2>  <ul class="*:rounded-full *:border *:border-sky-100 *:bg-sky-50 *:px-2 *:py-0.5 dark:text-sky-300 dark:*:border-sky-500/15 dark:*:bg-sky-500/10 ...">    <li>Sales</li>    <li>Marketing</li>    <li>SEO</li>    <!-- ... -->  </ul></div>
```

It's important to note that overriding a style with a utility directly on the child itself won't work due to the specificity of the generated child selector:

Won't work, children can't override their own styling.

```
<ul class="*:bg-sky-50 ...">  <li class="bg-red-50 ...">Sales</li>  <li>Marketing</li>  <li>SEO</li>  <!-- ... --></ul>
```

### Styling all descendants

Like*, the**variant can be used to style children of an element. The main difference is that**will apply styles toalldescendants, not just the direct children. This is especially useful when you combine it with another variant for narrowing the thing you're selecting:

```
<ul class="**:data-avatar:size-12 **:data-avatar:rounded-full ...">  {#each items as item}    <li>      <img src={item.src} data-avatar />      <p>{item.name}</p>    </li>  {/each}</ul>
```

## Custom variants

### Using arbitrary variants

Just likearbitrary valueslet you use custom values with your utility classes, arbitrary variants let you write custom selector variants directly in your HTML.

Arbitrary variants are just format strings that represent the selector, wrapped in square brackets. For example, this arbitrary variant changes the cursor tograbbingwhen the element has theis-draggingclass:

```
<ul role="list">  {#each items as item}    <li class="[&.is-dragging]:cursor-grabbing">{item}</li>  {/each}</ul>
```

Arbitrary variants can be stacked with built-in variants or with each other, just like the rest of the variants in Tailwind:

```
<ul role="list">  {#each items as item}    <li class="[&.is-dragging]:active:cursor-grabbing">{item}</li>  {/each}</ul>
```

If you need spaces in your selector, you can use an underscore. For example, this arbitrary variant selects allpelements within the element where you've added the class:

```
<div class="[&_p]:mt-4">  <p>Lorem ipsum...</p>  <ul>    <li>      <p>Lorem ipsum...</p>    </li>    <!-- ... -->  </ul></div>
```

You can also use at-rules like@mediaor@supportsin arbitrary variants:

```
<div class="flex [@supports(display:grid)]:grid">  <!-- ... --></div>
```

With at-rule custom variants the&placeholder isn't necessary, just like when nesting with a preprocessor.

### Registering a custom variant

If you find yourself using the same arbitrary variant multiple times in your project, it might be worth creating a custom variant using the@custom-variantdirective:

```
@custom-variant theme-midnight (&:where([data-theme="midnight"] *));
```

Now you can use thetheme-midnight:<utility>variant in your HTML:

```
<html data-theme="midnight">  <button class="theme-midnight:bg-black ..."></button></html>
```

Learn more about adding custom variants in theadding custom variants documentation.

## Appendix

### Quick reference

A quick reference table of every single variant included in Tailwind by default.

### Pseudo-class reference

This is a comprehensive list of examples for all the pseudo-class variants included in Tailwind to complement thepseudo-classes documentationat the beginning of this guide.

#### :hover

Style an element when the user hovers over it with the mouse cursor using thehovervariant:

```
<div class="bg-black hover:bg-white ...">  <!-- ... --></div>
```

#### :focus

Style an element when it has focus using thefocusvariant:

```
<input class="border-gray-300 focus:border-blue-400 ..." />
```

#### :focus-within

Style an element when it or one of its descendants has focus using thefocus-withinvariant:

```
<div class="focus-within:shadow-lg ...">  <input type="text" /></div>
```

#### :focus-visible

Style an element when it has been focused using the keyboard using thefocus-visiblevariant:

```
<button class="focus-visible:outline-2 ...">Submit</button>
```

#### :active

Style an element when it is being pressed using theactivevariant:

```
<button class="bg-blue-500 active:bg-blue-600 ...">Submit</button>
```

#### :visited

Style a link when it has already been visited using thevisitedvariant:

```
<a href="https://seinfeldquotes.com" class="text-blue-600 visited:text-purple-600 ..."> Inspiration </a>
```

#### :target

Style an element if its ID matches the current URL fragment using thetargetvariant:

```
<div id="about" class="target:shadow-lg ...">  <!-- ... --></div>
```

#### :first-child

Style an element if it's the first child using thefirstvariant:

```
<ul>  {#each people as person}    <li class="py-4 first:pt-0 ...">      <!-- ... -->    </li>  {/each}</ul>
```

#### :last-child

Style an element if it's the last child using thelastvariant:

```
<ul>  {#each people as person}    <li class="py-4 last:pb-0 ...">      <!-- ... -->    </li>  {/each}</ul>
```

#### :only-child

Style an element if it's the only child using theonlyvariant:

```
<ul>  {#each people as person}    <li class="py-4 only:py-0 ...">      <!-- ... -->    </li>  {/each}</ul>
```

#### :nth-child(odd)

Style an element if it's an oddly numbered child using theoddvariant:

```
<table>  {#each people as person}    <tr class="bg-white odd:bg-gray-100 ...">      <!-- ... -->    </tr>  {/each}</table>
```

#### :nth-child(even)

Style an element if it's an evenly numbered child using theevenvariant:

```
<table>  {#each people as person}    <tr class="bg-white even:bg-gray-100 ...">      <!-- ... -->    </tr>  {/each}</table>
```

#### :first-of-type

Style an element if it's the first child of its type using thefirst-of-typevariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="ml-2 first-of-type:ml-6 ...">      <!-- ... -->    </a>  {/each}</nav>
```

#### :last-of-type

Style an element if it's the last child of its type using thelast-of-typevariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="mr-2 last-of-type:mr-6 ...">      <!-- ... -->    </a>  {/each}  <button>More</button></nav>
```

#### :only-of-type

Style an element if it's the only child of its type using theonly-of-typevariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="mx-2 only-of-type:mx-6 ...">      <!-- ... -->    </a>  {/each}  <button>More</button></nav>
```

#### :nth-child()

Style an element at a specific position using thenthvariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="mx-2 nth-3:mx-6 nth-[3n+1]:mx-7 ...">      <!-- ... -->    </a>  {/each}  <button>More</button></nav>
```

#### :nth-last-child()

Style an element at a specific position from the end using thenth-lastvariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="mx-2 nth-last-3:mx-6 nth-last-[3n+1]:mx-7 ...">      <!-- ... -->    </a>  {/each}  <button>More</button></nav>
```

#### :nth-of-type()

Style an element at a specific position, of the same type using thenth-of-typevariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="mx-2 nth-of-type-3:mx-6 nth-of-type-[3n+1]:mx-7 ...">      <!-- ... -->    </a>  {/each}  <button>More</button></nav>
```

#### :nth-last-of-type()

Style an element at a specific position from the end, of the same type using thenth-last-of-typevariant:

```
<nav>  <img src="/logo.svg" alt="Vandelay Industries" />  {#each links as link}    <a href="#" class="mx-2 nth-last-of-type-3:mx-6 nth-last-of-type-[3n+1]:mx-7 ...">      <!-- ... -->    </a>  {/each}  <button>More</button></nav>
```

#### :empty

Style an element if it has no content using theemptyvariant:

```
<ul>  {#each people as person}    <li class="empty:hidden ...">{person.hobby}</li>  {/each}</ul>
```

#### :disabled

Style an input when it's disabled using thedisabledvariant:

```
<input class="disabled:opacity-75 ..." />
```

#### :enabled

Style an input when it's enabled using theenabledvariant, most helpful when you only want to apply another style when an element is not disabled:

```
<input class="enabled:hover:border-gray-400 disabled:opacity-75 ..." />
```

#### :checked

Style a checkbox or radio button when it's checked using thecheckedvariant:

```
<input type="checkbox" class="appearance-none checked:bg-blue-500 ..." />
```

#### :indeterminate

Style a checkbox or radio button in an indeterminate state using theindeterminatevariant:

```
<input type="checkbox" class="appearance-none indeterminate:bg-gray-300 ..." />
```

#### :default

Style an option, checkbox or radio button that was the default value when the page initially loaded using thedefaultvariant:

```
<input type="checkbox" class="default:outline-2 ..." />
```

#### :optional

Style an input when it's optional using theoptionalvariant:

```
<input class="border optional:border-red-500 ..." />
```

#### :required

Style an input when it's required using therequiredvariant:

```
<input required class="border required:border-red-500 ..." />
```

#### :valid

Style an input when it's valid using thevalidvariant:

```
<input required class="border valid:border-green-500 ..." />
```

#### :invalid

Style an input when it's invalid using theinvalidvariant:

```
<input required class="border invalid:border-red-500 ..." />
```

#### :user-valid

Style an input when it's valid and the user has interacted with it, using theuser-validvariant:

```
<input required class="border user-valid:border-green-500" />
```

#### :user-invalid

Style an input when it's invalid and the user has interacted with it, using theuser-invalidvariant:

```
<input required class="border user-invalid:border-red-500" />
```

#### :in-range

Style an input when its value is within a specified range limit using thein-rangevariant:

```
<input min="1" max="5" class="in-range:border-green-500 ..." />
```

#### :out-of-range

Style an input when its value is outside of a specified range limit using theout-of-rangevariant:

```
<input min="1" max="5" class="out-of-range:border-red-500 ..." />
```

#### :placeholder-shown

Style an input when the placeholder is shown using theplaceholder-shownvariant:

```
<input class="placeholder-shown:border-gray-500 ..." placeholder="you@example.com" />
```

#### :details-content

Style the content of a<details>element using thedetails-contentvariant:

```
<details class="details-content:bg-gray-100 ...">  <summary>Details</summary>  This is a secret.</details>
```

#### :autofill

Style an input when it has been autofilled by the browser using theautofillvariant:

```
<input class="autofill:bg-yellow-200 ..." />
```

#### :read-only

Style an input when it is read-only using theread-onlyvariant:

```
<input class="read-only:bg-gray-100 ..." />
```
