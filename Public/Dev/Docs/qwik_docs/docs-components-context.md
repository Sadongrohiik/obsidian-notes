# https://qwik.dev/docs/components/context/

[Original link](https://qwik.dev/docs/components/context/)

# Context

Qwik provides a context API, which solves the problem of props drilling and it is very similar to React's functional useContext(). In fact, Qwik's context API is the most efficient way to pass down data to different components, reducing overhead, generating less code, and allowing Qwik to more effectively treeshake unused data.

Qwik's context API is made of 3 methods, importable from @builder.io/qwik:

```
import { type Signal, component$, useSignal } from '@builder.io/qwik';
import {
  useContext,
  useContextProvider,
  createContextId,
} from '@builder.io/qwik';
 
export const ThemeContext = createContextId<Signal<string>>(
  'docs.theme-context'
);
 
export default component$(() => {
  const theme = useSignal('dark');
  useContextProvider(ThemeContext, theme);
  return (
    <>
      <button
        onClick$={() =>
          (theme.value = theme.value == 'dark' ? 'light' : 'dark')
        }
      >
        Flip
      </button>
      <Child />
    </>
  );
});
 
const Child = component$(() => {
  const theme = useContext(ThemeContext);
  return <div>Theme is {theme.value}</div>;
});
```

In the above example, a ContextId named docs.theme-context is created and used to provide a useSignal to the default component. The Child component uses the useContext method to get the useSignal and render its value.

## createContextId()

This method is used to create a new ContextId.

```
export interface GenericType {
  ...
}
 
export const QwikCityContext = createContextId<GenericType>(name: string): ContextId<GenericType>;
```

### Parameters

### Returns

Notice that the value returned by createContextId() does not hold any state, it is an immutable ID object i.e. { id: 'io.builder.qwik.city' }. It's only used to describe the name and type of the context, like an address or an identifier.  Since it doesn't hold any state, it can be initialized as a singleton and exported from a shared module.

## useContextProvider()

This method is used to create a Context for a specific component and its descendants, using the ContextId as the key identifier of the context.

```
import { component$, useStore, useContextProvider } from '@builder.io/qwik';
 
export const Parent = component$(() => {
 
  const qwikCityObject = useStore<GenericType>({
    ...
  });
 
  useContextProvider(QwikCityContext, qwikCityObject);
  useContextProvider(PlainArrayContext, [1, 2, 3])
  useContextProvider(AppNameContext, "My Qwik App")
 
  return (
    <Children />
  );
});
```

### Parameters

ContextId: A previously created Context must be supplied, serving as an identifier for the data being provided as the second parameter.

data: You can provide any data type, such as Qwik's ﻿useSignal, ﻿useStore, arrays, or objects.

### Caveats

## useContext()

This method is used to get the value of Context which is provided by Parent Component.

```
import { component$, useContext } from '@builder.io/qwik';
 
export const Children = component$(() => {
  const qwikCityObject = useContext(QwikCityContext);
  const plainArray = useContext(PlainArrayContext);
  const appName = useContext(AppNameContext);
 
  return (
    <div>Child components can use any of the provided values, such as {appName}</div>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
