# https://qwik.dev/docs/advanced/optimizer/

[Original link](https://qwik.dev/docs/advanced/optimizer/)

# Optimizer

Qwik's philosophy is to delay loading code for as long as possible. To do that, Qwik relies on an Optimizer to re-arrange the code for lazy loading. The Optimizer is a code level transformation that runs as part of the rollup.

The Optimizer is written in Rust (and available as WASM) for instant performance.

The Optimizer looks for $ and applies a transformation that extracts the expression following the $ and turns it into a lazy-loadable and importable symbol.

Let's start by looking at a simple Counter example:

```
export const Counter = component$(() => {
  const count = useSignal(0);
 
  return <button onClick$={() => count.value++}>{count.value}</button>;
});
```

The above code represents what a developer would write to describe the component. Below are the transformations that the Optimizer applies to the code to make the code lazy-loadable.

```
const Counter = component(qrl('./chunk-a.js', 'Counter_onMount'));
```

```
export const Counter_onMount = () => {
  const count = useSignal(0);
  return <button onClick$={qrl('./chunk-b.js', 'Counter_onClick', [count])}>{count.value}</button>;
};
```

```
const Counter_onClick = () => {
  const [count] = useLexicalScope();
  return count.value++;
};
```

Notice that every occurrence of $ results in a new lazy loadable symbol.

## Serialization

See serialization for a discussion of what is serializable.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
