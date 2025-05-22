# https://qwik.dev/docs/cookbook/sync-events/

[Original link](https://qwik.dev/docs/cookbook/sync-events/)

# sync$() Synchronous Events (BETA)

Qwik processes events asynchronously. This means that some APIs such as event.preventDefault() and event.stopPropagation() do not work as expected. To work around this limitation, Qwik provides a sync$() API which allows you to process events synchronously. But sync$() comes with a few caveats:

A typical way to deal with these limitations is to split the event handling into two parts:

Because sync$() can't access the state what is the best strategy to deal with it? The answer is to use element attributes to pass state into the sync$() function.

NOTE: If you only need to prevent the default behavior, you can simply use the standard preventDefault:{eventName} syntax. This is strictly for when you need to chain events together synchronously

## Example: sync$() with state

In this example, we have a behavior where we want to prevent the default behavior of the link based on some state. We do this by breaking the code into three parts:

```
import { component$, useSignal, sync$, $ } from '@builder.io/qwik';
 
export default component$(() => {
  const shouldPreventDefault = useSignal(true);
  return (
    <div>
      <div>Sync Event:</div>
      <input
        type="checkbox"
        checked={shouldPreventDefault.value}
        onChange$={(e, target) =>
          (shouldPreventDefault.value = target.checked)
        }
      />{' '}
      Should Prevent Default
      <hr />
      <a
        href="https://google.com"
        target="_blank"
        data-should-prevent-default={shouldPreventDefault.value}
        onClick$={[
          sync$((e: MouseEvent, target: HTMLAnchorElement) => {
            if (target.hasAttribute('data-should-prevent-default')) {
              e.preventDefault();
            }
          }),
          $(() => {
            console.log(
              shouldPreventDefault.value ? 'Prevented' : 'Not Prevented'
            );
          }),
        ]}
      >
        open Google
      </a>
    </div>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
