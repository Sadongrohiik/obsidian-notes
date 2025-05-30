# https://qwik.dev/docs/concepts/think-qwik/

[Original link](https://qwik.dev/docs/concepts/think-qwik/)

# Think Qwik

Qwik is very similar to other web frameworks at a high level. Qwik is a framework that renders a tree of components resulting in an interactive application.

The unique part of Qwik is not in what it does but in how it achieves its goals. Qwik's goal is to have instant-on applications, even on mobile devices. Qwik achieves this through two main strategies:

The goal of Qwik is having only to download and execute the bare minimum of the application.

## Delay Execution

Delay execution of JavaScript as much as possible.

Qwik applications startup fast because there is a minimal amount of JavaScript code to execute. (At its simplest, a Qwik application only needs about 1KB of JavaScript to become interactive.)

By aggressively delaying the application download and execution, Qwik can provide near-instant startup performance. No current generation of web frameworks can match this implementation.

Qwik is fast not because it uses clever algorithms but because it is designed in a way where most of the JavaScript never needs to be downloaded or executed. Its speed comes from not doing things (such as hydration) that other frameworks have to do.

## Resumability & Serialization

Resumability is discussed in detail here. Resumability allows Qwik applications to continue execution where the server left off. All frameworks need to keep track of internal data structures about the application's state. The current generation of frameworks does not preserve this information when transitioning from the server to the browser. As a result, the framework's data structures need to be rebuilt in the browser, duplicating the work that was done on the server. The rebuilding of data structures and attaching of listeners is called hydration.

Qwik serializes listeners, internal data structures, and application state into the HTML during the server-browser handoff. Because all of the information is serialized in HTML, the client can just resume execution where the server left off.

## What is the problem?

Modern websites require vast amounts of JavaScript to become interactive. Too much JavaScript manifests itself in two problems:

As applications get more complex with a higher fidelity of interactivity, the amount of code being shipped has steadily increased over the years, with no sign of stopping. Simply put, websites are getting more complicated. An increase in site complexity, in turn, requires more code. All of this code negatively impacts site startup performance.

To make matters worse, JavaScript is single-threaded; therefore, complex sites can't take advantage of modern multi-core CPUs.

### How did we get here?

The solution to the above problem is both obvious and hard: Ship less JavaScript.

The obvious part is that sites with less JavaScript will perform better.

The hard part is that our tools don't help us achieve this. Most of them solve problems in a way that makes shipping less JavaScript hard. These tools are designed to address specific issues without considering how much JavaScript they produce.

Do you need to solve rendering, styling, animation, A/B testing, analytics, etc.? There is a tool for that. Just import or add a <script> tag, and these tools will solve your problems, but at the expense of making the initial bundle bigger.

As an industry, the implication of bundle size has often been overlooked. Each tool solves a specific problem individually, but size is not part of the equation. Size becomes a problem when all the tools are combined, and by that point, there is very little the developer can do about it.

### What's the solution?

Qwik is designed from the ground up to address the size problem. Small bundle size is its initial goal, and all other design decisions are subservient to that goal.

Qwik is not about creating less JavaScript. Qwik is about not having to ship all of that JavaScript to the client at once on application startup. Qwik is what you end up with when you take the idea of "delay loading of JavaScript" to the extreme.

Yes, Qwik requires a different way of thinking and designing your application, but the result is near zero initial JavaScript with progressive JavaScript download based on user interactions.

### Size should not be a developer problem

Today, size is the developers' problem. If you follow best practices for each of the frameworks, tools, etc., you will have a large bundle size. It is at that time when developers start to mitigate the problem with some sort of lazy loading boundaries etc. (But as anyone who has done this will tell you: the options are limited.)

Industry best practices lead to large bundles, and the web is full of examples.

The mantra of Qwik is that bundle size should not be something that developers should think about. It should just naturally emerge as part of how the framework is designed.

Qwik is designed from the ground up to produce lots of lazy loadable boundaries. Tooling can break up your application into many lazy-loadable chunks, and the runtime can download them only when needed.

### Why not fix existing frameworks/tools?

In short, the lazy loading philosophy must be done at a low level and can not be retroactively added to the existing frameworks/tools without changing them fundamentally. Such fundamental change would be incompatible with the framework/tools and their respective ecosystems, rendering them useless.

When a framework makes certain assumptions, such as that all rendering is synchronous, adding asynchronous lazy loading becomes pretty close to impossible. Or, if a framework recovers the listener location from templates, then download and execution of those templates is a must before the site can be interactive. These are just some of the more obvious examples, but in practice, there is a long tail of endless reasons why the current mental model does not fit the requirements of resumability.

The above also means that it is not feasible for existing frameworks to add resumability as a feature. Existing frameworks will never be able to do what Qwik can (without breaking backward compatibility).

### Why are we building Qwik?

Because we believe there is a better way to build sites. A way that does not involve massive amounts of JavaScript that must be downloaded eagerly on startup before your site becomes interactive. A way that allows the developer to think about adding features rather than how to break up the huge codebase into smaller chunks. A way to have instant-on sites for a better user experience. And all of that, in a way that is independent of the size of the application codebase.

## Does page speed really matter?

Put simply: slow sites deter visitors, costing businesses millions. Fast sites have better SEO, better UX, and are more profitable.

Some examples from web.dev:

### Contributors

Thanks to all the contributors who have helped make this documentation better!
