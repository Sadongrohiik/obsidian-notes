# https://qwik.dev/docs/cookbook/streaming-deferred-loaders/

[Original link](https://qwik.dev/docs/cookbook/streaming-deferred-loaders/)

# Streaming/deferred loaders

When you use routeLoader$ the default behavior is to wait for it to complete before rendering our component(s).
However, there is a way to render the DOM up to the point where routeLoader$ is used and wait for it to complete.
By returning an asynchronous function from our routeLoader$ we can stream/defer the rendering to provide immediate visual feedback.

```
import { Resource, component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useMyData = routeLoader$(() => {
  return async () => {
    await delay(4_000);
    return 'MyData ' + Math.random();
  };
});
 
const delay = (timeout: number) => {
  return new Promise((res) => setTimeout(res, timeout));
};
 
export default component$(() => {
  const myData = useMyData();
  return (
    <>
      <div>BEFORE</div>
      <Resource
        value={myData}
        onResolved={(data) => <div>DATA: {data}</div>}
      />
      <div>AFTER</div>
    </>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
