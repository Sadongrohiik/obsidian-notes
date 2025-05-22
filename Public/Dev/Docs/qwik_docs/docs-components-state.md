# https://qwik.dev/docs/components/state/

[Original link](https://qwik.dev/docs/components/state/)

# State

State management is an important part of any app. In Qwik, there are two types of state, reactive and static:

It is important to notice that state in Qwik is not necessarily a local component state, but rather an app state that can be instantiated by any component.

## useSignal()

Use useSignal() to create a reactive signal (a form of state). The useSignal() takes an initial value and returns a reactive signal.

The reactive signal returned by useSignal() consists of an object with a single property .value. If you change the value property of the signal, any component that depends on it will be updated automatically.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const count = useSignal(0);
 
  return (
    <button onClick$={() => count.value++}>
      Increment {count.value}
    </button>
  );
});
```

This example above shows how useSignal() can be used in a counter component to keep track of the count. Modifying the count.value property will cause the component to be updated automatically. For instance, when the property is changed in the button click handler as in the example above.

NOTE If you just need to read the signal's value, don't pass the entire signal as a prop, instead pass only its value:

⛔ Avoid:

```
const isClosedSig = useSignal(false);
 
return <Child isClosed={isClosedSig} />;
```

✅ Instead do:

```
const isClosedSig = useSignal(false);
 
return <Child isClosed={isClosedSig.value} />;
```

## useStore()

Works very similarly to useSignal(), but it takes an object as its initial value and the reactivity extends to nested objects and arrays by default. One can think of a store as a multiple-value signal or an object made of several signals.

Use useStore(initialStateObject) hook to create a reactive object. It takes an initial object (or a factory function) and returns a reactive object.

```
import { component$, useStore } from '@builder.io/qwik';
 
export default component$(() => {
  const state = useStore({ count: 0, name: 'Qwik' });
 
  return (
    <>
      <button onClick$={() => state.count++}>Increment</button>
      <p>Count: {state.count}</p>
      <input
        value={state.name}
        onInput$={(_, el) => (state.name = el.value)}
      />
    </>
  );
});
```

NOTE For reactivity to work as expected, make sure to keep a reference to the reactive object and not only to its properties. e.g. doing let { count } = useStore({ count: 0 }) and then mutating count won't trigger updates of components that depend on the property.

Because useStore() tracks deep reactivity, that means that Arrays and Objects inside the store will also be reactive.

```
import { component$, useStore } from '@builder.io/qwik';
 
export default component$(() => {
  const store = useStore({
    nested: {
      fields: { are: 'also tracked' },
    },
    list: ['Item 1'],
  });
 
  return (
    <>
      <p>{store.nested.fields.are}</p>
      <button
        onClick$={() => {
          // Even though we are mutating a nested object, this will trigger a re-render
          store.nested.fields.are = 'tracked';
        }}
      >
        Clicking me works because store is deep watched
      </button>
      <br />
      <button
        onClick$={() => {
          // Because store is deep watched, this will trigger a re-render
          store.list.push(`Item ${store.list.length + 1}`);
        }}
      >
        Add to list
      </button>
      <ul>
        {store.list.map((item, key) => (
          <li key={key}>{item}</li>
        ))}
      </ul>
    </>
  );
});
```

Notice that for useStore() to track all nested properties, it needs to allocate a lot of Proxy objects. This can be a performance issue if you have a lot of nested properties. In that case, you can use the deep: false option to only track the top-level properties.

```
const shallowStore = useStore(
  {
    nested: {
      fields: { are: 'also tracked' }
    },
    list: ['Item 1'],
  },
  { deep: false }
);
```

Handling Dynamic Object Mutations

When dynamically manipulating object properties, such as deleting them while they are being rendered somewhere in the app, you may encounter issues.  This could happen if the component renders values dependent on an object's property that is currently being removed.  To prevent this situation, use optional chaining when accessing properties.  For example, if attempting to remove a property:

```
delete store.propertyName;
```

Be sure to access this property cautiously in the component by using optional chaining ( ?. ):

```
const propertyValue = store.propertyName?.value;
```

### Methods

To provide methods on the store, you must make them into QRLs and refer to the store with this, like so:

```
import { component$, useStore, $, type QRL } from "@builder.io/qwik";
 
type CountStore = { count: number; increment: QRL<(this: CountStore) => void> };
 
export default component$(() => {
  const state = useStore<CountStore>({
    count: 0,
    increment: $(function (this: CountStore) {
      this.count++;
    }),
  });
 
  return (
    <>
      <button onClick$={() => state.increment()}>Increment</button>
      <p>Count: {state.count}</p>
    </>
  );
});
```

Do you know why you should use a regular function(){} instead of an arrow function in useStore()? This is because arrow functions don't have their own bindings to this in JavaScript. This means that if you try to access this using an arrow function, this.count could point to another object's count 😱.

## Computed state

In Qwik, there are two ways to create computed values, each with a different use case (in order of preference):

useComputed$(): useComputed$() is the preferred way of creating computed values. Use it when the computed value can be derived synchronously purely from the source state (current application state). For example, creating a lowercase version of a string or combining first and last names into a full name.

useResource$(): useResource$() is used when the computed value is asynchronous or the state comes from outside of the application. For example, fetching the current weather (external state) based on a current location (application internal state).

In addition to the two ways of creating computed values described above, there is also a lower-level (useTask$()). This way does not produce a new signal, but rather modifies the existing state or produces a side effect.

### useComputed$()

Use useComputed$ to memoize a value derived synchronously from other state.

It is similar to memo in other frameworks, since it will only recompute the value when one of the input signals changes.

```
import { component$, useComputed$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const name = useSignal('Qwik');
  const capitalizedName = useComputed$(() => {
    // it will automatically reexecute when name.value changes
    return name.value.toUpperCase();
  });
 
  return (
    <>
      <input type="text" bind:value={name} />
      <p>Name: {name.value}</p>
      <p>Capitalized name: {capitalizedName.value}</p>
    </>
  );
});
```

NOTE Because useComputed$() is synchronous it is not necessary to explicitly track the input signals.

### useResource$()

Use useResource$() to create a computed value that is derived asynchronously. It's the asynchronous version of useComputed$(), which includes the state of the resource (loading, resolved, rejected) on top of the value.

A common use of useResource$() is to fetch data from an external API within the component, which can occur either on the server or the client.

The useResource$ hook is meant to be used with <Resource />. The <Resource /> component is a convenient way to render different UI based on the state of the resource.

```
import {
  component$,
  Resource,
  useResource$,
  useSignal,
} from '@builder.io/qwik';
 
export default component$(() => {
  const postId = useSignal('23');
 
  const postTitle = useResource$<string>(async ({ track }) => {
    // it will run first on mount (server), then re-run whenever postId changes (client)
    // this means this code will run on the server and the browser
    track(() => postId.value);
 
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/posts/${postId.value}`
    );
    const data = await response.json();
    return data.title as string;
  });
 
  return (
    <>
      <input type="number" bind:value={postId} max={100} min={0} />
      <h1>Post#{postId}:</h1>
      <Resource
        value={postTitle}
        onPending={() => <p>Loading...</p>}
        onResolved={(title) => <h2>{title}</h2>}
      />
    </>
  );
});
```

Note: The important thing to understand about useResource$ is that it executes on the initial component render (just like useTask$). Often times it is desirable to start fetching the data on the server as part of the initial HTTP request before the component is rendered. Fetching data as part of Server-Side Rendering (SSR) is a common and preferred method of data loading, typically handled by the routeLoader$ API. useResource$ is more of a low-level API that is useful when you want to fetch data in the browser.

In many ways useResource$ is similar to useTask$. The big differences are:

See routeLoader$ for fetching data early as part of initial HTTP request.

NOTE: During SSR the <Resource> component will pause rendering until the resource is resolved. This way the SSR will not render with the loading indicator.

#### Advanced example

A more complete example of fetching data with AbortController, track and cleanup. This example will fetch a list of jokes based on the query typed by the user,
automatically reacting to changes in the query, including aborting requests that are currently pending.

```
import {
  component$,
  useResource$,
  Resource,
  useSignal,
} from '@builder.io/qwik';
 
export default component$(() => {
  const query = useSignal('busy');
  const jokes = useResource$<{ value: string }[]>(
    async ({ track, cleanup }) => {
      track(() => query.value);
      // A good practice is to use `AbortController` to abort the fetching of data if
      // new request comes in. We create a new `AbortController` and register a `cleanup`
      // function which is called when this function re-runs.
      const controller = new AbortController();
      cleanup(() => controller.abort());
 
      if (query.value.length < 3) {
        return [];
      }
 
      const url = new URL('https://api.chucknorris.io/jokes/search');
      url.searchParams.set('query', query.value);
 
      const resp = await fetch(url, { signal: controller.signal });
      const json = (await resp.json()) as { result: { value: string }[] };
 
      return json.result;
    }
  );
 
  return (
    <>
      <label>
        Query: <input bind:value={query} />
      </label>
      <button>search</button>
      <Resource
        value={jokes}
        onPending={() => <>loading...</>}
        onResolved={(jokes) => (
          <ul>
            {jokes.map((joke, i) => (
              <li key={i}>{joke.value}</li>
            ))}
          </ul>
        )}
      />
    </>
  );
});
```

As we see in the example above, useResource$() returns a ResourceReturn<T> object that works like a reactive promise, containing the data and the resource state.

The state resource.loading can be one of the following:

The callback passed to useResource$() runs right after the useTask$() callbacks complete. Please refer to the Lifecycle section for more details.

#### <Resource />

<Resource /> is a component meant to be used with the useResource$() that renders different content depending on if the resource is pending, resolved, or rejected.

```
<Resource
  value={weatherResource}
  onPending={() => <div>Loading...</div>}
  onRejected={() => <div>Failed to load weather</div>}
  onResolved={(weather) => {
    return <div>Temperature: {weather.temp}</div>;
  }}
/>
```

It is worth noting that <Resource /> is not required when using useResource$(). It is just a convenient way to render the resource state.

This example shows how useResource$ is used to perform a fetch call to the agify.io API. This will guess a person's age based on the name typed by the user, and will update whenever the user types in the name input.

```
import {
  component$,
  useSignal,
  useResource$,
  Resource,
} from '@builder.io/qwik';
 
export default component$(() => {
  const name = useSignal<string>();
 
  const ageResource = useResource$<{
    name: string;
    age: number;
    count: number;
  }>(async ({ track, cleanup }) => {
    track(() => name.value);
    const abortController = new AbortController();
    cleanup(() => abortController.abort('cleanup'));
    const res = await fetch(`https://api.agify.io?name=${name.value}`, {
      signal: abortController.signal,
    });
    return res.json();
  });
 
  return (
    <section>
      <div>
        <label>
          Enter your name, and I'll guess your age!
          <input onInput$={(ev, el) => (name.value = el.value)} />
        </label>
      </div>
      <Resource
        value={ageResource}
        onPending={() => <p>Loading...</p>}
        onRejected={() => <p>Failed to person data</p>}
        onResolved={(ageGuess) => {
          return (
            <p>
              {name.value && (
                <>
                  {ageGuess.name} {ageGuess.age} years
                </>
              )}
            </p>
          );
        }}
      />
    </section>
  );
});
```

## Passing state

One of the nice features of Qwik is that the state can be passed to other components. Writing to the store will then only re-render the components which read from the store only.

There are two ways to pass state to other components:

### Using props

The simplest way to pass the state to other components is to pass it through props.

```
import { component$, useStore } from '@builder.io/qwik';
 
export default component$(() => {
  const userData = useStore({ count: 0 });
  return <Child userData={userData} />;
});
 
interface ChildProps {
  userData: { count: number };
}
export const Child = component$<ChildProps>(({ userData }) => {
  return (
    <>
      <button onClick$={() => userData.count++}>Increment</button>
      <p>Count: {userData.count}</p>
    </>
  );
});
```

### Using context

The context API is a way to pass state to components without having to pass it through props (i.e.: avoids prop drilling issues). Automatically, all the descendant components in the tree can access a reference to the state with read/write access to it.

Check the context API for more information.

```
import {
  component$,
  createContextId,
  useContext,
  useContextProvider,
  useStore,
} from '@builder.io/qwik';
 
// Declare a context ID
export const CTX = createContextId<{ count: number }>('stuff');
 
export default component$(() => {
  const userData = useStore({ count: 0 });
 
  // Provide the store to the context under the context ID
  useContextProvider(CTX, userData);
 
  return <Child />;
});
 
export const Child = component$(() => {
  const userData = useContext(CTX);
  return (
    <>
      <button onClick$={() => userData.count++}>Increment</button>
      <p>Count: {userData.count}</p>
    </>
  );
});
```

## noSerialize()

Qwik ensures that all application state is always serializable. This is important to ensure that Qwik applications have a resumability property.

Sometimes, it's necessary to store data that can't be serialized; noSerialize() instructs Qwik not to attempt serializing the marked value.
For example, a reference to a third-party library such as Monaco editor will always need noSerialize(), as it is not serializable.

If a value is marked as non-serializable, then that value will not survive serialization events, such as resuming the application on the client from SSR. In this situation, the value will be set to undefined and it is up to the developer to re-initialize the value on the client.

```
import {
  component$,
  useStore,
  useSignal,
  noSerialize,
  useVisibleTask$,
  type NoSerialize,
} from '@builder.io/qwik';
import type Monaco from './monaco';
import { monacoEditor } from './monaco';
 
export default component$(() => {
  const editorRef = useSignal<HTMLElement>();
  const store = useStore<{ monacoInstance: NoSerialize<Monaco> }>({
    monacoInstance: undefined,
  });
 
  useVisibleTask$(() => {
    const editor = monacoEditor.create(editorRef.value!, {
      value: 'Hello, world!',
    });
    // Monaco is not serializable, so we can't serialize it as part of SSR
    // We can however instantiate it on the client after the component is visible
    store.monacoInstance = noSerialize(editor);
  });
  return <div ref={editorRef}>loading...</div>;
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
