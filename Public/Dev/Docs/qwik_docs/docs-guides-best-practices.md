# https://qwik.dev/docs/guides/best-practices/

[Original link](https://qwik.dev/docs/guides/best-practices/)

# Best Practices

## Inline operations in templates

Qwik optimizer can better optimize the reactivity of the application if the operations are inlined in the template.

```
// Don't do this!
export default component$(() => {
  const signal = useSignal(0);
  const isBiggerThanZero = signal.value > 0 ? 'Bigger than zero' : 'Smaller than zero';
  return (
    <div>
      <button onClick$={() => signal.value++}>+</button>
      <button onClick$={() => signal.value--}>-</button>
      <div>{isBiggerThanZero} - Current value: { signal.value }</div>
    </div>
  );
});
```

The above implementation will cause the whole template to be re-rendered when the signal changes. This is because the isBiggerThanZero is not inlined in the template.

```
export default component$(() => {
  const signal = useSignal(0);
  return (
    <div>
      <button onClick$={() => signal.value++}>+</button>
      <button onClick$={() => signal.value--}>-</button>
        <div>
          {signal.value > 0 ? 'Bigger than zero' : 'Smaller than zero'} - Current
          value: {signal.value}
        </div>
    </div>
  );
});
```

## Moving signal reads to useTask$ or useComputed$

This is similar to the tip above.

Every time Qwik "reads" a signal/store value
the function that the "read" is happening at, will re-run again
on every change to that signal.

That’s why it’s better to "read" values (and track them)
inside of useTask$ or useComputed$ functions instead of inside component functions,
whenever possible.

Because otherwise, your component function will re-run
on each change.

```
// Don't do this!
export default component$(() => {
  const count = useSignal(1);
  const doubleCount = count.value*2;
  return (
    <div>{doubleCount}</div>
  );
});
```

The above implementation will cause the whole template to be re-rendered when the signal changes.

Below, only the useComputed$ function will re-run on any count.value change:

```
export default component$(() => {
  const count = useSignal(1);
  const dobuleCount = useComputed$(() => count.value*2);
  return (
    <div>{doubleCount.value}</div>
  );
});
```

## Use useVisibleTask$() as a last resort

Although convenient, useVisibleTask$() runs code eagerly and blocks the main thread, preventing user interaction until the task is finished. You can think of it as an escape hatch.

When in doubt, instead of "useVisibleTask$()" use:

Sometimes though, it is the only way to achieve the result.

In that case, you can add // eslint-disable-next-line qwik/no-use-visible-task to the line before "useVisibleTask$" to remove the warning.

### Register DOM events with useOn(), useOnWindow(), or useOnDocument()

Qwik allows to register event listeners in a declarative way, using the useOn() or using JSX.

When using useVisibleTask$() to programmatically register events, we are downloading and executing JavaScript eagerly, even if the event is not triggered.

```
// Don't do this!
useVisibleTask$(({ cleanup }) => {
  const listener = (event) => {
    const mouseEvent = event as MouseEvent;
    console.log(mouseEvent.x, mouseEvent.y);
  };
  document.addEventListener('mousemove', listener);
 
  cleanup(() => {
    document.removeEventListener('mousemove', listener);
  });
});
```

The above implementation causes more JavaScript to load eagerly, rather than responding precisely to user events. Increased upfront JavaScript loading results in slower app performance.

Instead, use the useOnDocument() hook to register events on the document object, this way Qwik will not execute any JS until the event is triggered.

```
useOnDocument(
  'mousemove',
  $((event) => {
    const mouseEvent = event as MouseEvent;
    console.log(mouseEvent.x, mouseEvent.y);
    // No manual clean up required!
  })
);
```

## Avoid accessing the location from the window object

Don't access window.location directly, use useLocation() hook instead.

```
// Don't do this!
useVisibleTask$(()=> {
    if (window.location.href).includes('foo') {
        //... do the thing
    }
})
// or
useTask$(() => {
  if (isBrowser) {
        if (window.location.href).includes('foo') {
        //... do the thing
    }
  }
})
```

Many actions related to location information can be executed during the initial server-side render, resulting in pure HTML without any JavaScript overhead.

Forcing this logic to run on the client side introduces increased upfront JavaScript and leads to eager loading.

```
// Do this!
const location = useLocation();
 
if (location.url.href.includes('foo')) {
  // Do the thing
}
```

### Exception

When using SSG for purely static files, it's inevitable to rely on the server without current location information during the build time.

However, exercise caution! If the required information (such as query parameters) isn't needed until a user event occurs, incorporate the check within your event handling code.

This approach helps to prevent eager loading of JavaScript and improves performance.

See: useLocation() Docs

### Contributors

Thanks to all the contributors who have helped make this documentation better!
