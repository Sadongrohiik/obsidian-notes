# https://tailwindcss.com/docs/styling-with-utility-classes

[Original link](https://tailwindcss.com/docs/styling-with-utility-classes)

## Overview

You style things with Tailwind by combining many single-purpose presentational classes(utility classes)directly in your markup:

You have a new message!

```
<div class="mx-auto flex max-w-sm items-center gap-x-4 rounded-xl bg-white p-6 shadow-lg outline outline-black/5 dark:bg-slate-800 dark:shadow-none dark:-outline-offset-1 dark:outline-white/10">  <img class="size-12 shrink-0" src="/img/logo.svg" alt="ChitChat Logo" />  <div>    <div class="text-xl font-medium text-black dark:text-white">ChitChat</div>    <p class="text-gray-500 dark:text-gray-400">You have a new message!</p>  </div></div>
```

For example, in the UI above we've used:

Styling things this way contradicts a lot of traditional best practices, but once you try it you'll quickly notice some really important benefits:

These benefits make a big difference on small projects, but they are even more valuable for teams working on long-running projects at scale.

### Why not just use inline styles?

A common reaction to this approach is wondering, “isn’t this just inline styles?” and in some ways it is — you’re applying styles directly to elements instead of assigning them a class name and then styling that class.

But using utility classes has many important advantages over inline styles, for example:

This component is fully responsive and includes a button with hover and active styles, and is built entirely with utility classes:

Erin Lindford

Product Engineer

```
<div class="flex flex-col gap-2 p-8 sm:flex-row sm:items-center sm:gap-6 sm:py-4 ...">  <img class="mx-auto block h-24 rounded-full sm:mx-0 sm:shrink-0" src="/img/erin-lindford.jpg" alt="" />  <div class="space-y-2 text-center sm:text-left">    <div class="space-y-0.5">      <p class="text-lg font-semibold text-black">Erin Lindford</p>      <p class="font-medium text-gray-500">Product Engineer</p>    </div>    <button class="border-purple-200 text-purple-600 hover:border-transparent hover:bg-purple-600 hover:text-white active:bg-purple-700 ...">      Message    </button>  </div></div>
```

## Thinking in utility classes

### Styling hover and focus states

To style an element on states like hover or focus, prefix any utility with the state you want to target, for examplehover:bg-sky-700:

Hover over this button to see the background color change

```
<button class="bg-sky-500 hover:bg-sky-700 ...">Save changes</button>
```

These prefixes are calledvariantsin Tailwind, and they only apply the styles from a utility class when the condition for that variant matches.

Here's what the generated CSS looks like for thehover:bg-sky-700class:

```
.hover\:bg-sky-700 {  &:hover {    background-color: var(--color-sky-700);  }}
```

Notice how this class does nothingunlessthe element is hovered? Itsonlyjob is to provide hover styles — nothing else.

This is different from how you'd write traditional CSS, where a single class would usually provide the styles for many states:

```
<button class="btn">Save changes</button><style>  .btn {    background-color: var(--color-sky-500);    &:hover {      background-color: var(--color-sky-700);    }  }</style>
```

You can even stack variants in Tailwind to apply a utility when multiple conditions match, like combininghover:anddisabled:

```
<button class="bg-sky-500 disabled:hover:bg-sky-500 ...">Save changes</button>
```

Learn more in the documentation styling elements onhover, focus, and other states.

### Media queries and breakpoints

Just like hover and focus states, you can style elements at different breakpoints by prefixing any utility with the breakpoint where you want that style to apply:

Resize this example to see the layout change

```
<div class="grid grid-cols-2 sm:grid-cols-3">  <!-- ... --></div>
```

In the example above, thesm:prefix makes sure thatgrid-cols-3only triggers at thesmbreakpoint and above, which is 40rem out of the box:

```
.sm\:grid-cols-3 {  @media (width >= 40rem) {    grid-template-columns: repeat(3, minmax(0, 1fr));  }}
```

Learn more in theresponsive designdocumentation.

### Targeting dark mode

Styling an element in dark mode is just a matter of adding thedark:prefix to any utility you want to apply when dark mode is active:

Light mode

Writes upside-down

The Zero Gravity Pen can be used to write in any orientation,
        including upside-down. It even works in outer space.

Dark mode

Writes upside-down

The Zero Gravity Pen can be used to write in any orientation,
        including upside-down. It even works in outer space.

```
<div class="bg-white dark:bg-gray-800 rounded-lg px-6 py-8 ring shadow-xl ring-gray-900/5">  <div>    <span class="inline-flex items-center justify-center rounded-md bg-indigo-500 p-2 shadow-lg">      <svg        class="h-6 w-6 text-white"        fill="none"        viewBox="0 0 24 24"        stroke="currentColor"        aria-hidden="true"      >        <!-- ... -->      </svg>    </span>  </div>  <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight ">Writes upside-down</h3>  <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm ">    The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.  </p></div>
```

Just like with hover states or media queries, the important thing to understand is that a single utility class will never includeboththe light and dark styles — you style things in dark mode by using multiple classes, one for the light mode styles and another for the dark mode styles.

```
.dark\:bg-gray-800 {  @media (prefers-color-scheme: dark) {    background-color: var(--color-gray-800);  }}
```

Learn more in thedark modedocumentation.

### Using class composition

A lot of the time with Tailwind you'll even use multiple classes to build up the value for a single CSS property, for example adding multiple filters to an element:

```
<div class="blur-sm grayscale">  <!-- ... --></div>
```

Both of these effects rely on thefilterproperty in CSS, so Tailwind uses CSS variables to make it possible to compose these effects together:

```
.blur-sm {  --tw-blur: blur(var(--blur-sm));  filter: var(--tw-blur,) var(--tw-brightness,) var(--tw-grayscale,);}.grayscale {  --tw-grayscale: grayscale(100%);  filter: var(--tw-blur,) var(--tw-brightness,) var(--tw-grayscale,);}
```

The generated CSS above is slightly simplified, but the trick here is that each utility sets a CSS variable just for the effect it's meant to apply. Then thefilterproperty looks at all of these variables, falling back to nothing if the variable hasn't been set.

Tailwind uses this same approach forgradients,shadow colors,transforms, and more.

### Using arbitrary values

Many utilities in Tailwind are driven bytheme variables, likebg-blue-500,text-xl, andshadow-md, which map to your underlying color palette, type scale, and shadows.

When you need to use a one-off value outside of your theme, use the special square bracket syntax for specifying arbitrary values:

```
<button class="bg-[#316ff6] ...">  Sign in with Facebook</button>
```

This can be useful for one-off colors outside of your color palette(like the Facebook blue above), but also when you need a complex custom value like a very specific grid:

```
<div class="grid grid-cols-[24rem_2.5rem_minmax(0,1fr)]">  <!-- ... --></div>
```

It's also useful when you need to use CSS features likecalc(), even if you are using your theme values:

```
<div class="max-h-[calc(100dvh-(--spacing(6)))]">  <!-- ... --></div>
```

There's even a syntax for generating completely arbitrary CSS including an arbitrary property name, which can be useful for setting CSS variables:

```
<div class="[--gutter-width:1rem] lg:[--gutter-width:2rem]">  <!-- ... --></div>
```

Learn more in the documentation onusing arbitrary values.

#### How does this even work?

Tailwind CSS isn't one big static stylesheet like you might be used to with other CSS frameworks — it generates the CSS needed based on the classes you're actually using when you compile your CSS.

It does this by scanning all of the files in your project looking for any symbol that looks like it could be a class name:

```
export default function Button({ size, children }) {  let sizeClasses = {    md: "px-4 py-2 rounded-md text-base",    lg: "px-5 py-3 rounded-lg text-lg",  }[size];  return (    <button type="button" className={`font-bold ${sizeClasses}`}>      {children}    </button>  );}
```

After it's found all of the potential classes, Tailwind generates the CSS for each one and compiles it all into one stylesheet of just the styles you actually need.

Since the CSS is generated based on the class name, Tailwind can recognize classes using arbitrary values likebg-[#316ff6]and generate the necessary CSS, even when the value isn't part of your theme.

Learn more about how this works indetecting classes in source files.

### Complex selectors

Sometimes you need to style an element under a combination of conditions, for example in dark mode, at a specific breakpoint, when hovered, and when the element has a specific data attribute.

Here's an example of what that looks like with Tailwind:

```
<button class="dark:lg:data-current:hover:bg-indigo-600 ...">  <!-- ... --></button>
```

```
@media (prefers-color-scheme: dark) and (width >= 64rem) {  button[data-current]:hover {    background-color: var(--color-indigo-600);  }}
```

Tailwind also supports things likegroup-hover, which let you style an element when a specific parent is hovered:

```
<a href="#" class="group rounded-lg p-8">  <!-- ... -->  <span class="group-hover:underline">Read more…</span></a>
```

```
@media (hover: hover) {  a:hover span {    text-decoration-line: underline;  }}
```

Thisgroup-*syntax works with other variants too, likegroup-focus,group-active, andmany more.

For really complex scenarios(especially when styling HTML you don't control), Tailwind supportsarbitrary variantswhich let you write any selector you want, directly in a class name:

```
<div class="[&>[data-active]+span]:text-blue-600 ...">  <span data-active><!-- ... --></span>  <span>This text will be blue</span></div>
```

```
div > [data-active] + span {  color: var(--color-blue-600);}
```

### When to use inline styles

Inline styles are still very useful in Tailwind CSS projects, particularly when a value is coming from a dynamic source like a database or API:

```
export function BrandedButton({ buttonColor, textColor, children }) {  return (    <button      style={{        backgroundColor: buttonColor,        color: textColor,      }}      className="rounded-md px-3 py-1.5 font-medium"    >      {children}    </button>  );}
```

You might also reach for an inline style for very complicated arbitrary values that are difficult to read when formatted as a class name:

```
<div class="grid-[2fr_max(0,var(--gutter-width))_calc(var(--gutter-width)+10px)]"><div style="grid-template-columns: 2fr max(0, var(--gutter-width)) calc(var(--gutter-width) + 10px)">  <!-- ... --></div>
```

Another useful pattern is setting CSS variables based on dynamic sources using inline styles, then referencing those variables with utility classes:

```
export function BrandedButton({ buttonColor, buttonColorHover, textColor, children }) {  return (    <button      style={{        "--bg-color": buttonColor,        "--bg-color-hover": buttonColorHover,        "--text-color": textColor,      }}      className="bg-(--bg-color) text-(--text-color) hover:bg-(--bg-color-hover) ..."    >      {children}    </button>  );}
```

## Managing duplication

When you build entire projects with just utility classes, you'll inevitably find yourself repeating certain patterns to recreate the same design in different places.

For example, here the utility classes for each avatar image are repeated five separate times:

#### Contributors

```
<div>  <div class="flex items-center space-x-2 text-base">    <h4 class="font-semibold text-slate-900">Contributors</h4>    <span class="bg-slate-100 px-2 py-1 text-xs font-semibold text-slate-700 ...">204</span>  </div>  <div class="mt-3 flex -space-x-2 overflow-hidden">    <img class="inline-block h-12 w-12 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" />    <img class="inline-block h-12 w-12 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" />    <img class="inline-block h-12 w-12 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.25&w=256&h=256&q=80" alt="" />    <img class="inline-block h-12 w-12 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" />    <img class="inline-block h-12 w-12 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" />  </div>  <div class="mt-3 text-sm font-medium">    <a href="#" class="text-blue-500">+ 198 others</a>  </div></div>
```

Don't panic! In practice this isn't the problem you might be worried it is, and the strategies for dealing with it are things you already do every day.

### Using loops

A lot of the time a design element that shows up more than once in the rendered page is only actually authored once because the actual markup is rendered in a loop.

For example, the duplicate avatars at the beginning of this guide would almost certainly be rendered in a loop in a real project:

#### Contributors

```
<div>  <div class="flex items-center space-x-2 text-base">    <h4 class="font-semibold text-slate-900">Contributors</h4>    <span class="bg-slate-100 px-2 py-1 text-xs font-semibold text-slate-700 ...">204</span>  </div>  <div class="mt-3 flex -space-x-2 overflow-hidden">    {#each contributors as user}      <img class="inline-block h-12 w-12 rounded-full ring-2 ring-white" src={user.avatarUrl} alt={user.handle} />    {/each}  </div>  <div class="mt-3 text-sm font-medium">    <a href="#" class="text-blue-500">+ 198 others</a>  </div></div>
```

When elements are rendered in a loop like this, the actual class list is only written once so there's no actual duplication problem to solve.

### Using multi-cursor editing

When duplication is localized to a group of elements in a single file, the easiest way to deal with it is to usemulti-cursor editingto quickly select and edit the class list for each element at once:

You'd be surprised at how often this ends up being the best solution. If you can quickly edit all of the duplicated class lists simultaneously, there's no benefit to introducing any additional abstraction.

```
<nav class="flex justify-center space-x-4">  <a href="/dashboard" class="font-medium rounded-lg px-3 py-2 text-gray-700 hover:bg-gray-100 hover:text-gray-900">    Home  </a>  <a href="/team" class="font-medium rounded-lg px-3 py-2 text-gray-700 hover:bg-gray-100 hover:text-gray-900">    Team  </a>  <a href="/projects" class="font-medium rounded-lg px-3 py-2 text-gray-700 hover:bg-gray-100 hover:text-gray-900">    Projects  </a>  <a href="/reports" class="font-medium rounded-lg px-3 py-2 text-gray-700 hover:bg-gray-100 hover:text-gray-900">    Reports  </a></nav>
```

### Using components

If you need to reuse some styles across multiple files, the best strategy is to create acomponentif you're using a front-end framework like React, Svelte, or Vue, or atemplate partialif you're using a templating language like Blade, ERB, Twig, or Nunjucks.

```
export function VacationCard({ img, imgAlt, eyebrow, title, pricing, url }) {  return (    <div>      <img className="rounded-lg" src={img} alt={imgAlt} />      <div className="mt-4">        <div className="text-xs font-bold text-sky-500">{eyebrow}</div>        <div className="mt-1 font-bold text-gray-700">          <a href={url} className="hover:underline">            {title}          </a>        </div>        <div className="mt-2 text-sm text-gray-600">{pricing}</div>      </div>    </div>  );}
```

Now you can use this component in as many places as you like, while still having a single source of truth for the styles so they can easily be updated together in one place.

### Using custom CSS

If you're using a templating language like ERB or Twig instead of something like React or Vue, creating a template partial for something as small as a button can feel like overkill compared to a simple CSS class likebtn.

While it's highly recommended that you create proper template partials for more complex components, writing some custom CSS is totally fine when a template partial feels heavy-handed.

Here's what abtn-primaryclass might look like, usingtheme variablesto keep the design consistent:

Save changes

```
<button class="btn-primary">Save changes</button>
```

```
@import "tailwindcss";@layer components {  .btn-primary {    border-radius: calc(infinity * 1px);    background-color: var(--color-violet-500);    padding-inline: --spacing(5);    padding-block: --spacing(2);    font-weight: var(--font-weight-semibold);    color: var(--color-white);    box-shadow: var(--shadow-md);    &:hover {      @media (hover: hover) {        background-color: var(--color-violet-700);      }    }  }}
```

Again though, for anything that's more complicated than just a single HTML element, we highly recommend using template partials so the styles and structure can be encapsulated in one place.

## Managing style conflicts

### Conflicting utility classes

When you add two classes that target the same CSS property, the class that appears later in the stylesheet wins. So in this example, the element will receivedisplay: grideven thoughflexcomes last in the actualclassattribute:

```
<div class="grid flex">  <!-- ... --></div>
```

```
.flex {  display: flex;}.grid {  display: grid;}
```

In general, you should just never add two conflicting classes to the same element — only ever add the one you actually want to take effect:

```
export function Example({ gridLayout }) {  return <div className={gridLayout ? "grid" : "flex"}>{/* ... */}</div>;}
```

Using component-based libraries like React or Vue, this often means exposing specific props for styling customizations instead of letting consumers add extra classes from outside of a component, since those styles will often conflict.

### Using the important modifier

When you really need to force a specific utility class to take effect and have no other means of managing the specificity, you can add!to the end of the class name to make all of the declarations!important:

```
<div class="bg-teal-500 bg-red-500!">  <!-- ... --></div>
```

```
.bg-red-500\! {  background-color: var(--color-red-500) !important;}.bg-teal-500 {  background-color: var(--color-teal-500);}
```

### Using the important flag

If you're adding Tailwind to a project that has existing complex CSS with high specificity rules, you can use theimportantflag when importing Tailwind to markallutilities as!important:

```
@import "tailwindcss" important;
```

```
@layer utilities {  .flex {    display: flex !important;  }  .gap-4 {    gap: 1rem !important;  }  .underline {    text-decoration-line: underline !important;  }}
```

### Using the prefix option

If your project has class names that conflict with Tailwind CSS utilities, you can prefix all Tailwind-generated classes and CSS variables using theprefixoption:

```
@import "tailwindcss" prefix(tw);
```

```
@layer theme {  :root {    --tw-color-red-500: oklch(0.637 0.237 25.331);  }}@layer utilities {  .tw\:text-red-500 {    color: var(--tw-color-red-500);  }}
```
