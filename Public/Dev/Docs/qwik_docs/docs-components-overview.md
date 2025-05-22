# https://qwik.dev/docs/components/overview/

[Original link](https://qwik.dev/docs/components/overview/)

# Components

Components are the basic building blocks of Qwik Applications. They are reusable pieces of code that can be used to build a UI.

Qwik components are unique in that:

## component$()

A Qwik component is a function that returns JSX wrapped in a component$ call.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return <div>Hello World!</div>;
});
```

The component$ function, marked by the trailing $, enables the Optimizer to split components into separate chunks.
This allows each chunk to be loaded independently as needed, rather than loading all components whenever the parent component is loaded.
Note: index.tsx, layout.tsx in routes folder, root.tsx and all entry files need export default. For other components you can use export const and export function.

### Composing Components

Components can be composed together to create more complex components.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return (
    <>
      <p>Parent Text</p>
      <Child />
    </>
  );
});
 
const Child = component$(() => {
  return <p>Child Text</p>;
});
```

Notice that Qwik components are already lazy loaded thanks to the $ sign. That means that you don't need to dynamically import the child component manually, Qwik will do it for you.

### Counter Example

A slightly more complex example of a counter.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const count = useSignal(0);
 
  return (
    <>
      <p>Count: {count.value}</p>
      <button onClick$={() => count.value++}>Increment</button>
    </>
  );
});
```

## Props

Props are used to pass data from the parent into the component. Data passed via props is accessible via the props argument to the component$ function.

Props are shallowly immutable, meaning primitive data types (strings, numbers, booleans) cannot be changed once passed. However, internal elements of reference types (objects, arrays, functions) can be changed despite the reference itself being immutable.

To change primitive props data in the parent component from the child component, use signals. When updating data locally within the child component a signal is not necessary, destructure the props and use the values to define new local variables.

The two examples below show a component Item that declares optional name, quantity, description, and price props.

In the first example, primitive data types are passed via props. The price prop is passed as a signal and can be changed from the parent component. quantity is passed as a number value that is used to define a new signal in Item that can be reactively updated locally. Alternatively, if quantity did not need to be reactive it could be defined as a normal variable instead of a signal.

```
import { component$, useSignal } from "@builder.io/qwik";
import type { Signal } from "@builder.io/qwik";
 
interface ItemProps {
  name?: string;
  quantity?: number;
  description?: string;
  price?: Signal<number>;
}
 
export const Item = component$<ItemProps>((props) => {
  const localQuantity = useSignal(props.quantity);
 
  return (
    <ul>
      <li>name: {props.name}</li>
      <li>quantity: {localQuantity}</li>
      <li>description: {props.description}</li>
      <li>price: {props.price}</li>
    </ul>
  );
});
 
export default component$(() => {
  const price = useSignal(9.99);
 
  return (
    <>
      <h1>Props</h1>
      <Item name="hammer" price={price} quantity={5} />
    </>
  );
});
```

In this second example, the props are passed as a single details object containing the data, instead of individual primitive values. This allows the data inside to be mutated without the use of signals. However, the details object storing the data is still immutable and cannot be changed once passed.

```
import { component$ } from "@builder.io/qwik";
 
interface ItemProps {
  details: {
    name?: string;
    quantity?: number;
    description?: string;
    price?: number;
  };
}
 
export const Item = component$((props: ItemProps) => {
  props.details.price = 4.99;
 
  return (
    <ul>
      <li>name: {props.details.name}</li>
      <li>quantity: {props.details.quantity}</li>
      <li>description: {props.details.description}</li>
      <li>price: {props.details.price}</li>
    </ul>
  );
});
 
export default component$(() => {
  return (
    <Item
      details={{ name: "hammer", quantity: 5, description: "", price: 9.99 }}
    />
  );
});
```

In the examples above, we are using component$<ItemProps> to provide an explicit type for the props. This is optional, but it allows the TypeScript compiler to check that the props are used correctly.

### Default props

You can use the destructuring pattern with props to provide default values.

```
interface Props {
  enabled?: boolean;
  placeholder?: string;
}
 
// We can use JS's destructuring of props to provide a default value.
export default component$<Props>(({enabled = true, placeholder = ''}) => {
  return (
    <input disabled={!enabled} placeholder={placeholder} />
  );
});
```

## Rendering on Reactivity

Qwik components are reactive. This means that they automatically update on a state change. There are two kinds of updates:

The thing to keep in mind is that when state changes, your component function may execute zero or more times depending on what the state is bound to. For this reason, the function should be idempotent and you should not rely on the number of times it executes.

A state change causes the component to get invalidated. When components get invalidated, they are added to the invalidation queue, which is flushed (rendered) on the next requestAnimationFrame. This acts as a form of coalescing for component rendering.

## Getting hold of DOM element

Use ref to get hold of a DOM element. Create a signal to store DOM element. Then pass the signal to the JSX ref property.

Getting a reference to DOM elements can be useful to calculate the element size (getBoundingClientRect), computed styles, initializing a WebGL canvas, or even wire-up some third-party library that interacts with DOM elements directly.

```
import { component$, useVisibleTask$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const width = useSignal(0);
  const height = useSignal(0);
  const outputRef = useSignal<Element>();
 
  useVisibleTask$(() => {
    if (outputRef.value) {
      const rect = outputRef.value.getBoundingClientRect();
      width.value = Math.round(rect.width);
      height.value = Math.round(rect.height);
    }
  });
 
  return (
    <section>
      <article
        ref={outputRef}
        style={{ border: '1px solid red', width: '100px' }}
      >
        Change text value here to stretch the box.
      </article>
      <p>
        The above red box is {height.value} pixels high and {width.value}{' '}
        pixels wide.
      </p>
    </section>
  );
});
```

## Accessing Elements by id Across Server and Client Environments

In server and client environments, elements must sometimes be accessed by their id. Use the useId() function to get a unique identifier for the current component that remains consistent across server-side rendering (SSR) and client-side operations. This is pivotal when server-rendered components need client-side scripting, such as:

In a microfrontends setup, where multiple fragments run concurrently, useId() ensures unique and consistent IDs across execution environments, eliminating conflicts.

```
import {
  component$,
  useId,
  useSignal,
  useVisibleTask$,
} from '@builder.io/qwik';
 
export default component$(() => {
  const elemIdSignal = useSignal<string | null>(null);
  const id = useId();
  const elemId = `${id}-example`;
  console.log('server-side id:', elemId);
 
  useVisibleTask$(() => {
    const elem = document.getElementById(elemId);
    elemIdSignal.value = elem?.getAttribute('id') || null;
    console.log('client-side id:', elemIdSignal.value);
  });
 
  return (
    <section>
      <div id={elemId}>
        Both server-side and client-side console should match this id:
        <br />
        <b>{elemIdSignal.value || null}</b>
      </div>
    </section>
  );
});
```

## Lazy Loading

The component also serves an important role when breaking parent-child relationships for bundling purposes.

```
export const Child = () => <span>child</span>;
 
const Parent = () => (
  <section>
    <Child />
  </section>
);
```

In the above example, referring to the Parent component implies a transitive reference to the Child component. When the bundler is creating a chunk, a reference to Parent necessitates bundling Child as well. (Parent internally refers to Child.) These transitive dependencies are a problem because it means that having a reference to the root component will transitively refer to the remainder of the application—something which Qwik tries to avoid explicitly.

To avoid the above problem we don't refer to components directly, instead, we refer to the lazy wrapper. This is created automatically by the component$() function.

```
import { component$ } from '@builder.io/qwik';
 
export const Child = component$(() => {
  return <p>child</p>;
});
 
export const Parent = component$(() => {
  return (
    <section>
      <Child />
    </section>
  );
});
 
export default Parent;
```

In the above example the Optimizer transforms the above to:

```
const Child = componentQrl(qrl('./chunk-a', 'Child_onMount'));
const Parent = componentQrl(qrl('./chunk-b', 'Parent_onMount'));
const Parent_onMount = () => qrl('./chunk-c', 'Parent_onRender');
const Parent_onRender = () => (
  <section>
    <Child />
  </section>
);
```

NOTE
For simplicity, not all of the transformations are shown; all resulting symbols are kept in the same file for succinctness.

Notice that after the Optimizer transforms the code, the Parent no longer directly references Child. This is important because it allows the bundler (and tree shakers) to freely move the symbols into different chunks without pulling the rest of the application with it.

So what happens when the Parent component needs to render a Child component, but the Child component has not yet been downloaded? First, the Parent component renders its DOM like so.

```
<main>
  <section>
    <!--qv--><!--/qv-->
  </section>
</main>
```

As you can see in the above example, the <!--qv--> acts as a marker where the Child component will be inserted once it is lazy-loaded.

## Inline Components

In addition to the standard component$() with all of it's lazy-loaded
properties, Qwik also supports lightweight (inline) components that act more
like components in traditional frameworks.

```
import { component$ } from '@builder.io/qwik';
 
// Inline component: declared using a standard function.
export const MyButton = (props: { text: string }) => {
  return <button>{props.text}</button>;
};
 
// Component: declared using `component$()`.
export default component$(() => {
  return (
    <p>
      Some text:
      <MyButton text="Click me" />
    </p>
  );
});
```

In the above example, MyButton is an inline component.
Unlike the standard component$(), inline components cannot be individually
lazy-loaded; instead, they are bundled with their parent component. In this case:

You can think of inline components as being inlined into the component where they are instantiated.

### Limitations

Inline components come with some limitations that the standard component$()
does not have. Inline components:

As the name implies, inline components are best used sparingly for
lightweight pieces of markup since they offer the convenience of being
bundled with the parent component.

## Polymorphic components

When you want to output a different type of element depending on props but default to a <div>, you can do it using something like this:

```
const Poly = component$(
  <C extends string | FunctionComponent = 'div'>({
    as,
    ...props
  }: { as?: C } & PropsOf<string extends C ? 'div' : C>) => {
    const Cmp = as || 'div';
    return (
      <Cmp {...props}>
        <Slot />
      </Cmp>
    );
  }
);
 
export const TestComponent = component$(() => {
  // These all work with correct types
  return (
    <>
      <Poly>Hello from a div</Poly>
      <Poly as="a" href="/blog">
        Blog
      </Poly>
      <Poly as="input" onInput$={(ev, el) => console.log(el.value)} />
      <Poly as={OtherComponent} someProp />
    </>
  );
});
```

Note the string extends C, this is only true when TypeScript cannot infer the type from the as prop allowing you to specify the default type.

## API Overview

### State

### Styles

### Events

### Tasks/Lifecycle

### Other

### Components

## See Also

### Contributors

Thanks to all the contributors who have helped make this documentation better!
