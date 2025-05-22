# https://qwik.dev/docs/concepts/progressive/

[Original link](https://qwik.dev/docs/concepts/progressive/)

# Progressive

Progressive is about downloading code according to the application's needs, without eagerly downloading the entire code base.

This connects  to the core principle of Qwik which focuses on delaying the loading and execution of JavaScript for as long as possible. Qwik needs to break up the application into many lazy loadable chunks to achieve that.

## Current state-of-the-art

Existing frameworks suffer from two problems:

The problem is that the frameworks need to reconcile their internal state with the DOM. And this means that at least once in the application hydration occurs. Frameworks are required to be able to do a full render to rebuild the framework's internal state. After the first render, the frameworks can be more surgical about their updates, but the damage has been done, the code has been downloaded. So, two issues now arise:

## Solution

Qwik's architecture takes full advantage of modern tooling to automate the problem of entry point generation. Developers can write components normally, while the Qwik optimizer will split the components into chunks and download them when needed.

In addition, the framework runtime does not need to download code that is not required for interactivity, even if the component is part of the render tree.

### Optimizer

Optimizer is a code transformation that extracts functions into top-level importable symbols, which allows the Qwik runtime to lazy-load the JavaScript on an as-needed basis.

The Optimizer and Qwik runtime work together to achieve the desired result of fine-grained lazy loading.

Without the Optimizer, either:

Qwik runtime must understand the Optimizer output. What needs to be understood here is that by breaking up the component into lazy-loadable chunks, the lazy loading requirement introduces asynchronous code into the framework. The framework has to be written differently to take asynchronicity into account. Existing frameworks assume that all code is available synchronously. This assumption prevents an easy insertion of lazy-loading into existing frameworks. (For example, when a new component is created, the framework assumes that its initialization code can be invoked in a synchronous fashion. If this is the first time component is referenced, then its code needs to be lazy-loaded, and therefore the framework must take that into account).

### Lazy-loading

Lazy-loading is asynchronous. Qwik is an asynchronous framework. Qwik understands that at any time, it may not have a reference to a callback, and therefore, it may need to lazy-load it. (In contrast, most existing frameworks assume that all of the code is available synchronously, making lazy-loading non-trivial).

In Qwik everything is lazy-loadable:

Lazy-loading is a core property of the framework and not an afterthought.

### Optimizer and $

Take a look at this example again:

```
// the `$` suffix for `component` indicates that the component should be
// lazy-loaded.
export const Counter = component$(() => {
  const count = useSignal(0);
 
  // the `$` suffix for `onClick` indicates that the implementation for
  // the handler should be lazy-loaded.
  return <button onClick$={() => count.value++}>{count.value}</button>;
});
```

Notice the presence of $ in the code. $ is a marker that tells the Optimizer that the function
following it should be lazy-loaded. The $ is a single character that hints to the Optimizer and the developer to let them know
that asynchronous lazy-loading occurs here.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
