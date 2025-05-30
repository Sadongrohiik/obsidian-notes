# https://qwik.dev/docs/components/rendering/

[Original link](https://qwik.dev/docs/components/rendering/)

# Rendering

Rendering is the process of updating the DOM based on changes in the state of the application and the component templates.

Qwik is unique because it knows how to render templates out-of-order asynchronously and in a fine-grained manner.

## JSX

Just like React, Qwik uses JSX to express the component's template. Notice that JSX is only syntax, under the hood, React and Qwik are completely different. JSX != VDOM.

Qwik presents a few differences from other JSX frameworks:

```
import { component$, useSignal } from '@builder.io/qwik';
 
export const MyComponent = component$((props) => {
  const count = useSignal(0);
  return (
    <>
      <button
        onClick$={() => {
          count.value = count.value + props.step;
        }}
      >
        Increment by {props.step}
      </button>
      <main
        class={{
          even: count.value % 2 === 0, // conditional class
          odd: count.value % 2 === 1,
        }}
      >
        <h1>Count: {count.value}</h1>
      </main>
    </>
  );
});
```

## Rendering Child Components

Qwik lazy loads components on an as-needed basis. To minimize the number of components to download, Qwik only descends into child components if the component's props have changed.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export const Parent = component$(() => {
  const count = useSignal(0);
 
  return (
    <>
      <button onClick$={() => (count.value += 1)}>Increment</button>
      <Child name={'World_' + count.value} />
    </>
  );
});
 
export const Child = component$((props: { name: string }) => {
  return <p>Hello {props.name}</p>;
});
```

In the above example, the Parent component passes a changing name property to the Child component. The Child component will only re-render when the count signal changes.

### Rendering a list of items

In many cases you'll want to render components by mapping an array in the render function with items.map(). It is required for every item of the list to have a unique key property passed to the first child of the mapping function. The key must be a string or number and must be unique within the list.

```
import { component$ } from '@builder.io/qwik';
 
export const Parent = component$(() => {
  return (
    <>
      {data.map(({ message, uniqueKey }) => (
        <div key={uniqueKey}>
          <p>{message}</p>
        </div>
      ))}
    </>
  );
});
```

Note: it is not recommended to use the array's index as the key unless you can guarantee that the data for a given key will always be the same. It is always preferred to use some unique identifier from the data as the key.

### Rendering Conditionally

Conditional rendering is done with the Javascipt ternary operator ?, the && operator, or just by using if statements.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  const show = useSignal(false);
  return (
    <>
      <button onClick$={() => show.value = !show.value}>Toggle</button>
      {show.value ? <h1>Visible</h1> : <h1>Hidden</h1>}
      {show.value && <div>Only show when it's visible</div>}
    </>
  );
});
```

### dangerouslySetInnerHTML

Qwik offers an attribute on HTML Elements called dangerouslySetInnerHTML as a replacement for calling innerHTML on the DOM.

Due to cross-site-scripting (XSS) possibilities when rendering untrustworthy content, you must use dangerouslySetInnerHTML as a reminder that this operation might be dangerous.

```
const htmlString = "<strong>hello</strong>";
<div dangerouslySetInnerHTML={htmlString}></div>
```

### bind Attribute

The bind attribute is a convenient API for two-way data binding of an <input> value to a Signal.

For checkbox inputs, you can use bind:checked, which binds the checked boolean to the specified signal.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const firstName = useSignal('');
  const acceptConditions = useSignal(false);
 
  return (
    <form>
      <input type="text" bind:value={firstName} />
      <input type="checkbox" bind:checked={acceptConditions} />
 
      <div>First name: {firstName.value}</div>
    </form>
  );
})
```

The API does not work with useStore since it does not return a signal. You can still use the manual approach, combining value and onInput$ as shown below.

The bind: is compiled away by the Qwik optimizer to a property set and an event handler, ie, it is just syntax sugar.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const count = useSignal(0);
  const firstName = useSignal('');
  const acceptConditions = useSignal(false);
 
  return (
    <form>
     {/* For number inputs, use `valueAsNumber` instead of `value` to get the numeric value directly */}
      <input type="number"
        value={count.value}
        onInput$={(_, el) => count.value = el.valueAsNumber }
      />
      <input type="text"
        value={firstName.value}
        onInput$={(_, el) => firstName.value = el.value }
      />
      <input type="checkbox"
        checked={acceptConditions.value}
        onChange$={(_, el) => acceptConditions.value = el.checked }
      />
      <div>First name: {firstName.value}</div>
    </form>
  );
})
```

This API ensures that the value of the input is always in sync with the value of the signal, no matter where the change comes from.

## Async Rendering

It is important for the rendering pipeline to be able to lazy load child components. Since lazy loading is an asynchronous operation, rendering must also be asynchronous. In practice, this means that the render() function must return a promise.

Most current-generation frameworks have a synchronous render() process. Synchronous rendering can't easily deal with asynchronous code loading, so synchronous rendering necessitates that all dependant components are eagerly present before rendering can commence.

## Render Batching

Whenever the state of the application changes, Qwik will schedule a render operation. The render operation will be scheduled to run after a macro-task (e.g. setTimeout(0)). This allows the application to batch multiple state changes into a single render operation.

In addition, because of the asynchronous nature of Qwik, all DOM writes are buffered and only flushed once all of the components have been downloaded and their JSX functions executed. The result is that the UI will update as an atomic operation, and the user will not see the intermediate steps, even if the application is slow to render.

The end goal is to enable performance and consistent rendering, even in the context of fast changing state and slow network.

## Fine-grained Reactivity

Thanks to the fine-grained reactivity of Qwik, only the components that depend on the state will be updated. This is a big performance gain for two reasons:

### Contributors

Thanks to all the contributors who have helped make this documentation better!
