# https://qwik.dev/docs/components/tasks/

[Original link](https://qwik.dev/docs/components/tasks/)

# Tasks

Tasks are meant for running asynchronous operations as part of component initialization or change of component state.

Note: Tasks are similar to useEffect() in React, but there are enough differences that we did not want to call them the same so as not to bring preexisting expectations about how they work. The main differences are:

useTask$() should be your default go-to API for running either synchronous or asynchronous work as part of component initialization or state change. It is only when you can't achieve what you need with useTask$() that you should consider using useVisibleTask$() or useResource$().

The basic use case for useTask$() is to perform work on component initialization. useTask$() has these properties:

Tasks can also be used to perform work when a component state changes. In this case, the task will rerun every time the tracked state changes. See: track().

Sometimes a task needs to run only on the browser and after rendering, in that case, you should use useVisibleTask$().

Note: If you need to fetch data asynchronously and not block rendering, you should use useResource$().  useResource$() does not block rendering while the resource is being resolved.

## Lifecycle

Resumability is "Lazy execution", it's the ability to build the "framework state" (component boundaries, etc) on the server, and have it exist on the client without re-executing the framework again.

The application environment—whether client-side or server-side—is determined by user interactions. In server-side rendering, the application initially renders on the server.
When the user interacts with the application, it resumes on the client-side, continuing from the state left by the server. This approach ensures efficient and responsive user experiences by leveraging both environments based on interaction.

Note: For systems that use hydration, the execution of the application happens twice. Once on a server (SSR/SSG) and once on the browser (hydration). This is why many frameworks have "effects" which only execute on the browser. That means that the code that runs on the server is different than the code that runs on the browser. Qwik execution is unified, meaning if the code has already been executed on the server, it does not re-execute it on the browser.

In Qwik, there are only 3 lifecycle stages:

```
useTask$ -------> RENDER ---> useVisibleTask$
                            |
| --- SERVER or BROWSER --- | ----- BROWSER ----- |
                            |
                       pause|resume
```

SERVER: Usually the life of a component starts on the server (during SSR or SSG), in that case, the useTask$ and RENDER will run in the server, and then the VisibleTask will run in the browser, after the component is visible.

Notice that because the component was mounted in the server, only useVisibleTask$() runs in the browser. This is because the browser continues the same lifecycle, that was paused in the server right after the render and resumed in the browser.

BROWSER: When a component is first mounted or rendered in the browser, for example when a user navigates to a new page in a Single Page Application (SPA) or when a "modal" component initially appears on the page, the lifecycle will proceed as follows:

```
useTask$ --> RENDER --> useVisibleTask$
 
| -------------- BROWSER --------------- |
```

Notice that the lifecycle is exactly the same, but this time all the hooks run in the browser, and not in the server.

## useTask$()

useTask$() registers a hook to be executed upon component creation, it will run at least once either in the server or in the browser, depending on where the component is initially rendered.

Additionally, this task can be reactive and will re-execute when tracked state changes.

Notice that any subsequent re-execution of the task will always happen in the browser, because reactivity is a browser-only thing.

```
(state change) -> (re-execute)
                                  ^            |
                                  |            v
 useTask$(track) -> RENDER ->  CLICK  -> useTask$(track)
                        |
  | ----- SERVER ------ | ----------- BROWSER ----------- |
                        |
                   pause|resume
```

If useTask$() does not track any state, it will run exactly once, either in the server or in the browser (not both), depending where the component is initially rendered. Effectively behaving like an "on-mount" hook.

useTask$() will block the rendering of the component until after its async callback resolves, in other words, tasks execute sequentially even if they are asynchronous. (Only one task executes at a time).

Take a look at the simplest use case of the task to run some asynchronous work on component initialization:

```
import { component$, useSignal, useTask$ } from '@builder.io/qwik';
 
export default component$(() => {
  const fibonacci = useSignal<number[]>();
 
  useTask$(async () => {
    const size = 40;
    const array = [];
    array.push(0, 1);
    for (let i = array.length; i < size; i++) {
      array.push(array[i - 1] + array[i - 2]);
      await delay(100);
    }
    fibonacci.value = array;
  });
 
  return <p>{fibonacci.value?.join(', ')}</p>;
});
 
const delay = (time: number) => new Promise((res) => setTimeout(res, time));
```

In this example

Notice that useTask$() runs on the server BEFORE the actual rendering. Therefore if you need to do DOM manipulation, use useVisibleTask$() instead, which runs on the browser after rendering.

Use useTask$() when you need to:

Note, if you're thinking about loading data using fetch() inside of useTask$, consider using useResource$() instead. This API is more efficient in terms of leveraging SSR streaming and parallel data fetching.

### On mount

In Qwik, there isn't a specific "mount" step like in some other frameworks. Instead, components just start up directly where they're needed, either on a web server or in your browser.
This is without the inner track function, which is used to monitor specific pieces of data.

useTask$ runs always at least once when the component is first mounted.

```
import { component$, useTask$ } from '@builder.io/qwik';
 
export default component$(() => {
 
  useTask$(async () => {
    // A task without `track` any state effectively behaves like a `on mount` hook.
    console.log('Runs once when the component mounts in the server OR client.');
  });
 
  return <div>Hello</div>;
});
```

One unique aspect of Qwik, is that components are mounted only once across the server and client. This is a property of resumability. What this means is that if useTask$ is executed during Server-Side Rendering (SSR), it will not run again in the browser because Qwik does not perform hydration.

### track()

There are times when it is desirable to re-run a task when a component state changes. This is done by using the track() function. The track() function allows you to set up a dependency on a component's state when initially rendered on the server, and then re-execute the task when the state changes in the browser.

Track accepts signals, stores and functions. It returns the value of the signal, the store itself, or the function call result.

When you pass a store, the track will be called when the store gets or removes properties as well as mutations of properties.
Note that deep store updates don't mutate the store itself, so store[item].count++ will not trigger an update. Instead, you should individually track each store[item] (which are also automatically created stores).

During SSR, each component will wait until all tasks are completed before outputting the HTML for that component. So a task can be called multiple times during SSR if the tracked state changes due to other tasks.

Note: If all you want to do is compute a new state from an existing state synchronously, you should use useComputed$() instead.

```
import { component$, useSignal, useTask$ } from '@builder.io/qwik';
import { isServer } from '@builder.io/qwik';
 
export default component$(() => {
  const text = useSignal('Initial text');
  const delayText = useSignal('');
 
  useTask$(({ track }) => {
    // Passing a signal directly is more efficient than using a function.
    const newText = track(text);
    const update = () => (delayText.value = newText);
    isServer
      ? update() // don't delay on server render value as part of SSR
      : delay(500).then(update); // Delay in browser
  });
 
  return (
    <section>
      <label>
        Enter text: <input bind:value={text} />
      </label>
      <p>Delayed text: {delayText}</p>
    </section>
  );
});
 
const delay = (time: number) => new Promise((res) => setTimeout(res, time));
```

On the server:

On the browser:

The useTask$()

Sometimes it is required to only run code either in the server or in the client. This can be achieved by using the isServer and isBrowser booleans exported from @builder.io/qwik as shown above.

### track() as a function

In the above example, track() was used to track a specific signal. However, track() can also be used as a function to track multiple signals at once.

```
import { component$, useSignal, useTask$ } from '@builder.io/qwik';
import { isServer } from '@builder.io/qwik';
 
export default component$(() => {
  const isUppercase = useSignal(false);
  const text = useSignal('');
  const delayText = useSignal('');
 
  useTask$(({ track }) => {
    const value = track(() =>
      isUppercase.value ? text.value.toUpperCase() : text.value.toLowerCase()
    );
    const update = () => (delayText.value = value);
    isServer
      ? update() // don't delay on server render value as part of SSR
      : delay(500).then(update); // Delay in browser
  });
 
  return (
    <section>
      <label>
        Enter text: <input bind:value={text} />
      </label>
      <label>
        Is uppercase? <input type="checkbox" bind:checked={isUppercase} />
      </label>
      <p>Delay text: {delayText}</p>
    </section>
  );
});
 
function delay(time: number) {
  return new Promise((resolve) => setTimeout(resolve, time));
}
```

In this example, the track() takes a function that not only reads the signal but also transforms its value to uppercase/lowercase. The track() subscribes to multiple signals and computes their value.

### cleanup()

Sometimes when running a task, cleanup work needs to be performed. When a new task is triggered, the previous task's cleanup() callback is invoked. This callback is also invoked when the component is removed from the DOM.

This example shows how to implement a debounce feature using the cleanup() function.

```
import { component$, useSignal, useTask$ } from '@builder.io/qwik';
 
export default component$(() => {
  const text = useSignal('');
  const debounceText = useSignal('');
 
  useTask$(({ track, cleanup }) => {
    const value = track(() => text.value);
    const id = setTimeout(() => (debounceText.value = value), 500);
    cleanup(() => clearTimeout(id));
  });
 
  return (
    <section>
      <label>
        Enter text: <input bind:value={text} />
      </label>
      <p>Debounced text: {debounceText}</p>
    </section>
  );
});
```

## useVisibleTask$()

Sometimes a task needs to run only on the browser and after rendering, in that case, you should use useVisibleTask$(). The useVisibleTask$() is similar to useTask$() but it only runs on the browser and after initial rendering. useVisibleTask$() registers a hook to be executed when the component becomes visible in the viewport, it will run at least once in the browser, and it can be reactive and re-execute when some tracked state changes.

useVisibleTask$() has these properties:

Caution: The useVisibleTask$() should be used as a last resort, because it eagerly executes code on the client. Qwik, through resumability, goes out of its way to delay the execution of code on the client, and useVisibleTask$() is an escape hatch that should be used with caution. See Best Practices for more details.
If you need to run a task on a client consider useTask$() with a server guard.

```
import { component$, useSignal, useTask$ } from '@builder.io/qwik';
import { isServer } from '@builder.io/qwik';
 
export default component$(() => {
  const text = useSignal('Initial text');
  const isBold = useSignal(false);
 
  useTask$(({ track }) => {
    track(() => text.value);
    if (isServer) {
      return; // Server guard
    }
    isBold.value = true;
    delay(1000).then(() => (isBold.value = false));
  });
 
  return (
    <section>
      <label>
        Enter text: <input bind:value={text} />
      </label>
      <p style={{ fontWeight: isBold.value ? 'bold' : 'normal' }}>
        Text: {text}
      </p>
    </section>
  );
});
 
const delay = (time: number) => new Promise((res) => setTimeout(res, time));
```

In the above example, the useTask$() is guarded by isServer. The track() function is placed before the guard, which
allows the server to set up the subscription without executing any code on the server. The client
then executes the useTask$() once the text signal changes.

This example shows how to use useVisibleTask$() to initialize a clock on the browser only when the clock component becomes visible.

```
import {
  component$,
  useSignal,
  useVisibleTask$,
  type Signal,
} from '@builder.io/qwik';
 
export default component$(() => {
  const isClockRunning = useSignal(false);
 
  return (
    <>
      <div style="position: sticky; top:0">
        Scroll to see clock. (Currently clock is
        {isClockRunning.value ? ' running' : ' not running'}.)
      </div>
      <div style="height: 200vh" />
      <Clock isRunning={isClockRunning} />
    </>
  );
});
 
const Clock = component$<{ isRunning: Signal<boolean> }>(({ isRunning }) => {
  const time = useSignal('paused');
  useVisibleTask$(({ cleanup }) => {
    isRunning.value = true;
    const update = () => (time.value = new Date().toLocaleTimeString());
    const id = setInterval(update, 1000);
    cleanup(() => clearInterval(id));
  });
  return <div>{time}</div>;
});
```

Notice how the clock's useVisibleTask$() does not run until the <Clock> component becomes visible. The default behavior of useVisibleTask$() is to run the task when the component becomes visible.  This behavior is implemented through intersection observers.

Note:
The intersection observers will not run on components that are not considered visible such as <audio />.

### Option eagerness

At times it is desirable to run useVisibleTask$() eagerly as soon as the application is loaded in the browser. In that case, the useVisibleTask$() needs to run in eager mode. This is done by using the { strategy: 'document-ready' }.

```
import {
  component$,
  useSignal,
  useVisibleTask$,
  type Signal,
} from '@builder.io/qwik';
 
export default component$(() => {
  const isClockRunning = useSignal(false);
 
  return (
    <>
      <div style="position: sticky; top:0">
        Scroll to see clock. (Currently clock is
        {isClockRunning.value ? ' running' : ' not running'}.)
      </div>
      <div style="height: 200vh" />
      <Clock isRunning={isClockRunning} />
    </>
  );
});
 
const Clock = component$<{ isRunning: Signal<boolean> }>(({ isRunning }) => {
  const time = useSignal('paused');
  useVisibleTask$(
    ({ cleanup }) => {
      isRunning.value = true;
      const update = () => (time.value = new Date().toLocaleTimeString());
      const id = setInterval(update, 1000);
      cleanup(() => clearInterval(id));
    },
    { strategy: 'document-ready' }
  );
  return <div>{time}</div>;
});
```

In this example, the clock starts running immediately on the browser regardless of whether it is visible or not.

### Advanced: Time of running, and managing visibility with CSS

Internally, useVisibleTask$ is implemented by adding an attribute to the first rendered component (either the returned component or in the case of a Fragment, its first child).  With the standard eagerness, this means that if the first rendered component is hidden, the task will not run.

This means that you can use CSS to influence when the task runs. For example, if the task should only run on a mobile device, you can return a <div class="md:invisible" /> (in the case of Tailwind CSS).

This also means you cannot unhide a component using a visible task; for that you can return a Fragment:

```
return (<>
  <div />
  <MyHiddenComponent hidden={!showSignal.value} />
</>)
```

## Use Hook Rules

When using lifecycle hooks, you must adhere to the following rules:

```
useHook(); // <-- ❌ does not work
 
export default component$(() => {
  useCustomHook(); // <-- ✅ does work
  if (condition) {
    useHook(); // <-- ❌ does not work
  }
  useTask$(() => {
    useNavigate(); // <-- ❌ does not work
  });
  const myQrl = $(() => useHook()); // <-- ❌ does not work
  return <button onClick$={() => useHook()}></button>; // <-- ❌ does not work
});
 
function useCustomHook() {
  useHook(); // <-- ✅ does work
  if (condition) {
    useHook(); // <-- ❌ does not work
  }
}
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
