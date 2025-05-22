# https://tailwindcss.com/docs/responsive-design

[Original link](https://tailwindcss.com/docs/responsive-design)

## Overview

Every utility class in Tailwind can be applied conditionally at different breakpoints, which makes it a piece of cake to build complex responsive interfaces without ever leaving your HTML.

First, make sure you've added theviewport meta tagto the<head>of your document:

```
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

Then to add a utility but only have it take effect at a certain breakpoint, all you need to do is prefix the utility with the breakpoint name, followed by the:character:

```
<!-- Width of 16 by default, 32 on medium screens, and 48 on large screens --><img class="w-16 md:w-32 lg:w-48" src="..." />
```

There are five breakpoints by default, inspired by common device resolutions:

This works forevery utility class in the framework, which means you can change literally anything at a given breakpoint — even things like letter spacing or cursor styles.

Here's a simple example of a marketing page component that uses a stacked layout on small screens, and a side-by-side layout on larger screens:

```
<div class="mx-auto max-w-md overflow-hidden rounded-xl bg-white shadow-md md:max-w-2xl">  <div class="md:flex">    <div class="md:shrink-0">      <img        class="h-48 w-full object-cover md:h-full md:w-48"        src="/img/building.jpg"        alt="Modern building architecture"      />    </div>    <div class="p-8">      <div class="text-sm font-semibold tracking-wide text-indigo-500 uppercase">Company retreats</div>      <a href="#" class="mt-1 block text-lg leading-tight font-medium text-black hover:underline">        Incredible accommodation for your team      </a>      <p class="mt-2 text-gray-500">        Looking to take your team away on a retreat to enjoy awesome food and take in some sunshine? We have a list of        places to do just that.      </p>    </div>  </div></div>
```

Here's how the example above works:

We've only used one breakpoint in this example, but you could easily customize this component at other sizes using thesm,lg,xl, or2xlresponsive prefixes as well.

## Working mobile-first

Tailwind uses a mobile-first breakpoint system, similar to what you might be used to in other frameworks like Bootstrap.

What this means is that unprefixed utilities (likeuppercase) take effect on all screen sizes, while prefixed utilities (likemd:uppercase) only take effect at the specified breakpointand above.

### Targeting mobile screens

Where this approach surprises people most often is that to style something for mobile, you need to use the unprefixed version of a utility, not thesm:prefixed version. Don't think ofsm:as meaning "on small screens", think of it as "at the smallbreakpoint".

Don't usesm:to target mobile devices

```
<!-- This will only center text on screens 640px and wider, not on small screens --><div class="sm:text-center"></div>
```

Use unprefixed utilities to target mobile, and override them at larger breakpoints

```
<!-- This will center text on mobile, and left align it on screens 640px and wider --><div class="text-center sm:text-left"></div>
```

For this reason, it's often a good idea to implement the mobile layout for a design first, then layer on any changes that make sense forsmscreens, followed bymdscreens, etc.

### Targeting a breakpoint range

By default, styles applied by rules likemd:flexwill apply at that breakpoint and stay applied at larger breakpoints.

If you'd like to apply a utilityonlywhen a specific breakpoint range is active, stack a responsive variant likemdwith amax-*variant to limit that style to a specific range:

```
<div class="md:max-xl:flex">  <!-- ... --></div>
```

Tailwind generates a correspondingmax-*variant for each breakpoint, so out of the box the following variants are available:

### Targeting a single breakpoint

To target a single breakpoint, target the range for that breakpoint by stacking a responsive variant likemdwith themax-*variant for the next breakpoint:

```
<div class="md:max-lg:flex">  <!-- ... --></div>
```

Read abouttargeting breakpoint rangesto learn more.

## Using custom breakpoints

### Customizing your theme

Use the--breakpoint-*theme variables to customize your breakpoints:

```
@import "tailwindcss";@theme {  --breakpoint-xs: 30rem;  --breakpoint-2xl: 100rem;  --breakpoint-3xl: 120rem;}
```

This updates the2xlbreakpoint to use100reminstead of the default96rem, and creates newxsand3xlbreakpoints that can be used in your markup:

```
<div class="grid xs:grid-cols-2 3xl:grid-cols-6">  <!-- ... --></div>
```

Note that it's important to always use the same unit for defining your breakpoints or the generated utilities may be sorted in an unexpected order, causing breakpoint classes to override each other in unexpected ways.

Tailwind usesremfor the default breakpoints, so if you are adding additional breakpoints to the defaults, make sure you useremas well.

Learn more about customizing your theme in thetheme documentation.

### Removing default breakpoints

To remove a default breakpoint, reset its value to theinitialkeyword:

```
@import "tailwindcss";@theme {  --breakpoint-2xl: initial;}
```

You can also reset all of the default breakpoints using--breakpoint-*: initial, then define all of your breakpoints from scratch:

```
@import "tailwindcss";@theme {  --breakpoint-*: initial;  --breakpoint-tablet: 40rem;  --breakpoint-laptop: 64rem;  --breakpoint-desktop: 80rem;}
```

Learn more removing default theme values in thetheme documentation.

### Using arbitrary values

If you need to use a one-off breakpoint that doesn’t make sense to include in your theme, use theminormaxvariants to generate a custom breakpoint on the fly using any arbitrary value.

```
<div class="max-[600px]:bg-sky-300 min-[320px]:text-center">  <!-- ... --></div>
```

Learn more about arbitrary value support in thearbitrary valuesdocumentation.

## Container queries

### What are container queries?

Container queriesare a modern CSS feature that let you style something based on the size of a parent element instead of the size of the entire viewport. They let you build components that are a lot more portable and reusable because they can change based on the actual space available for that component.

### Basic example

Use the@containerclass to mark an element as a container, then use variants like@smand@mdto style child elements based on the size of the container:

```
<div class="@container">  <div class="flex flex-col @md:flex-row">    <!-- ... -->  </div></div>
```

Just like breakpoint variants, container queries are mobile-first in Tailwind CSS and apply at the target container size and up.

### Max-width container queries

Use variants like@max-smand@max-mdto apply a style below a specific container size:

```
<div class="@container">  <div class="flex flex-row @max-md:flex-col">    <!-- ... -->  </div></div>
```

### Container query ranges

Stack a regular container query variant with a max-width container query variant to target a specific range:

```
<div class="@container">  <div class="flex flex-row @sm:@max-md:flex-col">    <!-- ... -->  </div></div>
```

### Named containers

For complex designs that use multiple nested containers, you can name containers using@container/{name}and target specific containers with variants like@sm/{name}and@md/{name}:

```
<div class="@container/main">  <!-- ... -->  <div class="flex flex-row @sm/main:flex-col">    <!-- ... -->  </div></div>
```

This makes it possible to style something based on the size of a distant container, rather than just the nearest container.

### Using custom container sizes

Use the--container-*theme variables to customize your container sizes:

```
@import "tailwindcss";@theme {  --container-8xl: 96rem;}
```

This adds a new8xlcontainer query variant that can be used in your markup:

```
<div class="@container">  <div class="flex flex-col @8xl:flex-row">    <!-- ... -->  </div></div>
```

Learn more about customizing your theme in thetheme documentation.

### Using arbitrary values

Use variants like@min-[475px]and@max-[960px]for one-off container query sizes you don't want to add to your theme:

```
<div class="@container">  <div class="flex flex-col @min-[475px]:flex-row">    <!-- ... -->  </div></div>
```

### Using container query units

Usecontainer query length unitslikecqwas arbitrary values in other utility classes to reference the container size:

```
<div class="@container">  <div class="w-[50cqw]">    <!-- ... -->  </div></div>
```

### Container size reference

By default, Tailwind includes container sizes ranging from 16rem(256px)to 80rem(1280px):
