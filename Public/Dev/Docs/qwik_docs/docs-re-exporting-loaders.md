# https://qwik.dev/docs/re-exporting-loaders/

[Original link](https://qwik.dev/docs/re-exporting-loaders/)

# Re-exporting loaders

routeAction$ and routeLoader$ are typically declared in route boundary files such as layout.tsx, index.tsx and plugin.tsx inside the routesDir directory
here is docs.

Sometimes you would like to declare them outside of the route boundaries.
This may be useful when you want to create reusable logic or a library.
In such a case, it is essential that this function is re-exported from within the router boundary otherwise it will not run or throw exception.

## Solution

You can define routeAction$ and routeLoader$ in your custom path and re-export them in your layout.tsx, index.tsx and plugin.tsx files.

### Reusable logic example

Let's imagine we have a routeLoader$ that checks whether our user is logged in or not.
It wouldn't make sense to copy and paste the same code into many parts of our code to make it work.
As per good practices, the ideal method is to centralize the logic.
Here in this example we declare routeAction$ and routeLoader$ in a centralized file so we can then reuse it in our files.

Example with ./shared/loaders.ts

```
import { routeAction$, routeLoader$ } from '@builder.io/qwik-city';
 
export const useCommonRouteAction = routeAction$(async () => {
  // ...
  return { success: true, data: ['Qwik', 'Partytown'] };
});
 
export const useCommonRouteLoader = routeLoader$(async () => {
  // ...
  return ['Mitosis', 'Builder.io'];
});
```

Now you can use your common routeAction$ and routeLoader$ in paths like this one ./src/routes/index.tsx.

```
import { component$ } from '@builder.io/qwik';
import { Form } from '@builder.io/qwik-city';
import { useCommonRouteAction, useCommonRouteLoader } from './shared/loaders';
 
// As mentioned, here we are re-exporting them
export { useCommonRouteAction, useCommonRouteLoader } from './shared/loaders';
 
export default component$(() => {
  const commonRouteAction = useCommonRouteAction();
  const commonRouteLoader = useCommonRouteLoader();
 
  return (
    <div class="flex justify-around text-xl">
      <Form action={commonRouteAction}>
        <div class="mb-2">CommonRouteAction</div>
        <div class="mb-4">response:</div>
        <div class="text-lg font-bold mb-4">
          {commonRouteAction.value?.data.join(' ') || ''}
        </div>
        <button type="submit">Submit</button>
      </Form>
      <div>
        <div class="mb-2">CommonRouteLoader</div>
        <div class="mb-4">response:</div>
        <div class="text-lg font-bold mb-4">{commonRouteLoader.value.join(' ')}</div>
      </div>
    </div>
  );
});
```

### Third-party libraries example

It may happen that we need to integrate third-party libraries over which we have no control over how it works.
Let's think for example about integrating a payment method into our application.
We are provided with a component to integrate into the page, but we have no control over what happens under the hood of this component.
Here, if this library needs routeAction$ or routeLoader$ we must re-export them to allow the correct functioning of our library.

#### Here is our code:

```
import { component$ } from '@builder.io/qwik';
import { ThirdPartyPaymentComponent, useThirdPartyPaymentLoader } from './third-party-library';
 
// As mentioned, here we are re-exporting the third-party loader
export { useThirdPartyPaymentLoader } from './third-party-library';
 
export default component$(() => {
  return (
    <section>
      <ThirdPartyPaymentComponent />
    </section>
  );
});
```

#### Here is the library code:

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useThirdPartyPaymentLoader = routeLoader$(() => {
  return { name: 'John Doe' };
});
 
export const ThirdPartyPaymentComponent = component$(() => {
  const thirdPartyPaymentLoader = useThirdPartyPaymentLoader();
  return (
    <div
      class={[
        'w-96 h-56 m-auto rounded-xl relative text-white font-bold shadow-2xl',
        'transition-transform transform hover:scale-110 bg-gray-600',
      ]}
    >
      <div class="w-full px-8 absolute top-8">
        <div class="flex justify-between">
          <div class="">
            <p>Name</p>
            <p class="tracking-widest">{thirdPartyPaymentLoader.value.name}</p>
          </div>
          <img class="w-12 h-12" src="/logos/qwik-logo.svg" />
        </div>
        <div class="pt-1">
          <p class="font-medium">Card Number</p>
          <p class="tracking-wider">4642 3489 9867 7632</p>
        </div>
        <div class="pt-6 pr-6">
          <div class="flex justify-between text-xs">
            <div>
              <p class="font-medium">Valid</p>
              <p class="tracking-wider">11/15</p>
            </div>
            <div>
              <p class="font-medium">Expiry</p>
              <p class="tracking-wider">03/25</p>
            </div>
            <div>
              <p class="font-medium">CVV</p>
              <p class="tracking-wider">···</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
