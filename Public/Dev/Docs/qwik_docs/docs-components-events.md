# https://qwik.dev/docs/components/events/

[Original link](https://qwik.dev/docs/components/events/)

# Events

For a web application to be interactive, there needs to be a way to respond to user events. This is done by registering callback functions in the JSX template. Event handlers are registered using the on{EventName}$ attribute. For example, the onClick$ attribute is used to listen for click events.

```
<button onClick$={() => alert('CLICKED!')}>click me!</button>
```

## Inline Handler

In the following example, the onClick$ attribute of the <button> element is used to let Qwik know that a callback () => store.count++ should be executed whenever the click event is fired by the <button>.

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

You can also use bind:propertyName to conveniently have a two-way binding between a signal and an input element.

Notice that onClick$ ends with $. This is a hint to both the Optimizer and the developer that a special transformation occurs at this location. The presence of the $ suffix implies a lazy-loaded boundary here. The code associated with the click handler is not loaded into the JavaScript Virtual Machine (VM) until the user activates the click event. However, to avoid delays during the first interaction, it is eagerly loaded into the browser cache.

In real-world applications, the listener may refer to complex code. By creating a lazy-loaded boundary (with the $), Qwik can tree-shake all of the code behind the click listener and delay its loading until the user clicks the button.

## Reusing Event Handlers

To reuse the same event handler for multiple elements or events, you have to wrap the event handler into the $() function exported by @builder.io/qwik. This transforms it into a QRL.

```
import { component$, useSignal, $ } from '@builder.io/qwik';
 
export default component$(() => {
  const count = useSignal(0);
  const increment = $(() => count.value++);
  return (
    <>
      <button onClick$={increment}>Increment</button>
      <p>Count: {count.value}</p>
    </>
  );
});
```

Note: If you extract the event handler, you must manually wrap it in the $(...handler...). This ensures that it is lazily attached.

## Multiple Event Handlers

To register multiple event handlers for the same event, you can pass an array of event handlers to the on{EventName}$ attribute.

```
import { component$, useSignal, $ } from '@builder.io/qwik';
 
export default component$(() => {
  const count = useSignal(0);
  const print = $((ev) => console.log('CLICKED!', ev));
  const increment = $(() => count.value++);
 
  // The button when clicked will print "CLICKED!" to the console, increment the count and send an event to Google Analytics.
  return (
    <button
      onClick$={[print, increment, $(() => {
        ga.send('click', { label: 'increment' });
      })]}
    >
      Count: {count.value}
    </button>
  );
});
```

## Event Object

The first argument of the event handler is the Event object. This object contains information about the event that triggered the handler. For example, the Event object for a click event contains information about the mouse position and the element that was clicked. You can check out the MDN docs to know more details about each DOM event.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const position = useSignal<{ x: number; y: number }>();
  return (
    <div
      onClick$={(event) => (position.value = { x: event.x, y: event.y })}
      style="height: 100vh"
    >
      <p>
        Clicked at: ({position.value?.x}, {position.value?.y})
      </p>
    </div>
  );
});
```

## Asynchronous Events

Due to Qwik's asynchronous nature, the execution of an event handler might be delayed if the implementation has not yet been loaded into the JavaScript VM. Consequently, the following APIs on an Event object will not work:

### preventDefault & stopPropagation

Because event handling is asynchronous, you can't use event.preventDefault() or event.stopPropagation(). To solve this, Qwik introduces a declarative way to prevent default through preventdefault:{eventName} and stoppropagation:{eventName} attributes.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return (
    <a
      href="/docs"
      preventdefault:click // This will prevent the default behavior of the "click" event.
      stoppropagation:click // This will stop the propagation of the "click" event.
      onClick$={() => {
        // event.PreventDefault() will not work here, because handler is dispatched asynchronously.
        alert('Do something else to simulate navigation...');
      }}
    >
      Go to docs page
    </a>
  );
});
```

### Event Target

Because event handling is asynchronous, you can't use event.currentTarget. To solve this, Qwik handlers provide a currentTarget as a second argument.

```
import { component$, useSignal } from '@builder.io/qwik';
 
export default component$(() => {
  const currentElm = useSignal<HTMLElement|null>(null);
  const targetElm = useSignal<HTMLElement|null>(null);
 
  return (
    <section onClick$={(event, currentTarget) => {
      currentElm.value = currentTarget;
      targetElm.value = event.target as HTMLElement;
    }}>
      Click on any text <code>target</code> and <code>currentElm</code> of the event.
      <hr/>
      <p>Hello <b>World</b>!</p>
      <hr/>
      <ul>
        <li>currentElm: {currentElm.value?.tagName}</li>
        <li>target: {targetElm.value?.tagName}</li>
      </ul>
    </section>
  );
});
```

Note: currentTarget in the DOM points to the element that the event listener was attached to. In the example above it will always be the <SECTION> element.

### Synchronous Event Handling

In some cases, it is necessary to handle an event traditionally, because some APIs need to be used synchronously. For example, dragstart event must be processed synchronously and therefore it can't be combined with Qwik's lazy code execution.

To do this, you can leverage a useVisibleTask to programmatically add an event listener using the DOM API directly.

```
import { component$, useSignal, useVisibleTask$ } from '@builder.io/qwik';
 
export default component$(() => {
  const draggableRef = useSignal<HTMLElement>();
  const dragStatus = useSignal('');
 
  useVisibleTask$(({ cleanup }) => {
    if (draggableRef.value) {
      // Use the DOM API to add an event listener.
      const dragstart = () => (dragStatus.value = 'dragstart');
      const dragend = () => (dragStatus.value = 'dragend');
 
      draggableRef.value!.addEventListener('dragstart', dragstart);
      draggableRef.value!.addEventListener('dragend', dragend);
      cleanup(() => {
        draggableRef.value!.removeEventListener('dragstart', dragstart);
        draggableRef.value!.removeEventListener('dragend', dragend);
      });
    }
  });
 
  return (
    <div>
      <div draggable ref={draggableRef}>
        Drag me!
      </div>
      <p>{dragStatus.value}</p>
    </div>
  );
});
```

NOTE Using VisibleTask to listen for events is an anti-pattern in Qwik because it causes eager execution of code in the browser defeating resumability. Only use it when you have no other choice. You should use JSX to listen for events, for example: <div onClick$={...}>. Alternatively, if you need to listen to events programmatically, consider using the useOn(...) event methods.

## Custom Event Props

When creating your components, it is often useful to pass custom event props that resemble event handlers, even though they are just callbacks and not actual DOM events. Component boundaries in Qwik must be serializable for the optimizer to split them up into separate chunks. Functions are not serializable unless they are converted to a QRL.

For example, listening for triple click events, which html cannot do by default, would require creating an onTripleClick$ custom event prop.

```
import { component$, Slot, useStore } from '@builder.io/qwik';
 
export default component$(() => {
  return (
    <Button onTripleClick$={() => alert('TRIPLE CLICKED!')}>
      Triple Click me!
    </Button>
  );
});
 
type ButtonProps = {
  onTripleClick$: QRL<() => void>;
};
 
export const Button = component$<ButtonProps>(({ onTripleClick$ }) => {
  const state = useStore({
    clicks: 0,
    lastClickTime: 0,
  });
  return (
    <button
      onClick$={() => {
        // triple click logic
        const now = Date.now();
        const timeBetweenClicks = now - state.lastClickTime;
        state.lastClickTime = now;
        if (timeBetweenClicks > 500) {
          state.clicks = 0;
        }
        state.clicks++;
        if (state.clicks === 3) {
          // handle custom event
          onTripleClick$();
          state.clicks = 0;
        }
      }}
    >
      <Slot />
    </button>
  );
});
```

Notice the use of the QRL type in onTripleClick$: QRL<() => void>;. It is like wrapping a function in $() but at the type level. If you had const greet = $(() => "hi 👋"); and hovered over 'greet', you would see that 'greet' is of type QRL<() => "hi 👋">

## Window and Document Events

So far, the discussion has focused on listening to events originating from elements. There are events such as scroll and mousemove that need to be listened to on the window or document. Qwik allows this by providing the document:on and window:on prefixes when listening for events.

The window:on/document: prefixes are used to register an event at the current DOM location of the component while allowing it to receive events from the window/document. There are two advantages to this:

## useOn[window|document] Hook

useOn[window|document]() hook will add a DOM-based event listener at the component level programmatically. This is often useful when you want to create your own use hooks or if you don't know the event name at the time of compilation.

```
import { $, component$, useOnDocument, useStore } from '@builder.io/qwik';
 
// Assume reusable use method that does not have access to JSX
// but needs to register event handlers.
function useMousePosition() {
  const position = useStore({ x: 0, y: 0 });
  useOnDocument(
    'mousemove',
    $((event) => {
      const { x, y } = event as MouseEvent;
      position.x = x;
      position.y = y;
    })
  );
  return position;
}
 
export default component$(() => {
  const pos = useMousePosition();
  return (
    <div>
      MousePosition: ({pos.x}, {pos.y})
    </div>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
