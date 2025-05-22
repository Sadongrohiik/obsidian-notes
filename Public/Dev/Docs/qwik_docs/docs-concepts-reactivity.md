# https://qwik.dev/docs/concepts/reactivity/

[Original link](https://qwik.dev/docs/concepts/reactivity/)

# Reactivity

Reactivity allows Qwik to track which components are subscribed to which state. This information enables Qwik to invalidate only the relevant component on state change, which minimizes the number of components that need to be re-rendered.

Without fine-grained reactivity, a state change would require re-rendering from the root component, which would force the whole component tree to be eagerly downloaded.

It's important to notice that Qwik does not do change detection like Angular. Instead, Qwik relies on signals to surgically update the component templates when the relevant state changes, without having to dirty-check the whole state.

## Proxy

Reactivity requires that the framework keeps track of the relationship between the state of the application and the components. The framework must render the whole application at least once to build the reactivity graph. The build of this reactivity graph initially happens on the server and is serialized to HTML so that the browser can use the information without being forced to do a single pass through all components to rebuild the graph. (Qwik does not need to do hydration to register events or build up the reactivity graph).

Reactivity can be done in a few ways:

Qwik uses proxies for a few reasons:

Because of the above constraints, Qwik uses proxies to keep track of the reactivity graph.

## Counter Example

```
export const Counter = component$(() => {
  const store = useStore({ count: 0 });
 
  return <button onClick$={() => store.count++}>{store.count}</button>;
});
```

## Unsubscribe example

```
export const ComplexCounter = component$(() => {
  const store = useStore({ count: 0, visible: true });
 
  return (
    <>
      <button onClick$={() => (store.visible = !store.visible)}>
        {store.visible ? 'hide' : 'show'}
      </button>
      <button onClick$={() => store.count++}>increment</button>
      {store.visible ? <p>{store.count}</p> : null}
    </>
  );
});
```

This example is a more complicated counter.

Notice how the set of subscriptions automatically updates as the component renders different branches of its JSX. The advantage of the proxy is that the subscriptions update automatically as the applications execute, and the system can always compute the smallest set of invalidated components.

## Deep objects

So far, the examples show the store (useStore()) was a simple object with primitive values.

```
export const MyComp = component$(() => {
  const store = useStore({
    person: { first: null, last: null },
    location: null
  });
 
  store.location = {street: 'main st'};
 
  return (
    <section>
      <p>{store.person.last}, {store.person.first}</p>
      <p>{store.location.street}</p>
    </section>
  );
})
```

In the above examples, Qwik will automatically wrap child objects person and location into a proxy and correctly create subscriptions on all deep properties.

The wrapping behavior described above has one surprising side-effect. Writing and reading from a proxy auto wraps the object, which means that the identity of the object changes. This should normally not be an issue, but it is something that the developer should keep in mind.

```
export const MyComp = component$(() => {
  const store = useStore({ person: null });
  const person = { first: 'John', last: 'Smith' };
  store.person = person; // store.person auto wraps object into proxy
 
  if (store.person !== person) {
    // The consequence of auto wrapping is that the object identity changes.
    console.log('store auto-wrapped person into a proxy');
  }
});
```

## Out-of-order rendering

Qwik components are rendered out of order. A component can be rendered without forcing a parent component to be rendered first or a child components to be rendered as a consequence of the component render. This is an important property of Qwik because it allows Qwik applications to only re-render components which have been invalidated due to a state change rather than re-rendering the whole component tree on a state change.

When components are rendered, they need to have access to their props. Parent components create props. The props must be serializable for the component to render independently from the parent.

## Invalidating child components

When re-rendering a component, the child component's props either stay the same or are updated. A child component only invalidates if its props change.

```
export const Child = component$((props: { count: number }) => {
  return <span>{props.count}</span>;
});
 
export const MyApp = component$(() => {
  const store = useStore({ a: 0, b: 0, c: 0 });
 
  return (
    <>
      <button onClick$={() => store.a++}>a++</button>
      <button onClick$={() => store.b++}>b++</button>
      <button onClick$={() => store.c++}>c++</button>
      {JSON.stringify(store)}
 
      <Child count={store.a} />
      <Child count={store.b} />
    </>
  );
});
```

In the above example, there are two <Child/> components.

Notice that the child components only re-render when their props change. This is an important property of Qwik applications as it significantly limits the amount of re-rendering the application must do on some state change. While less re-rendering has performance benefits, the real benefit is that large portions of the applications do not get downloaded if they don't need to be re-rendered.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
