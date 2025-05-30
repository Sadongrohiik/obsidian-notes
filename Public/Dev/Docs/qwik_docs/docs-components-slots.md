# https://qwik.dev/docs/components/slots/

[Original link](https://qwik.dev/docs/components/slots/)

# Slots

Slots allow a component to treat the JSX children of the component as a form of input and project these children into the component's DOM tree.

This concept has different names in different frameworks:

The main API to achieve this is the <Slot> component, exported in @builder.io/qwik:

```
import { Slot, component$ } from '@builder.io/qwik';
 
const Button = component$(() => {
  return (
    <button>
      Content: <Slot />
    </button>
  );
});
 
export default component$(() => {
  return (
    <Button>
      This goes inside {'<Button>'} component marked by{`<Slot>`}
    </Button>
  );
});
```

The <Slot> component is a placeholder for the children of the component. The <Slot> component will be replaced by the children of the component during rendering.

Note: Slots in Qwik are declarative, allowing Qwik to render parents and children in isolation. Because slots are declarative, the children can NOT be read, or transformed by the components.

Slots in Qwik act like designated placeholders for content, allowing components to stay independent and avoid unnecessary re-renders. This setup keeps things flexible and easy to manage, unlike the direct children approach where parent changes can lead to frequent and complex child updates. Slots help maintain a smooth and efficient component structure.

In unique situations where some work needs to be done based on children, and the drawbacks of parents and children being lazy loaded together are understood, then an inline component is another choice.

### Named Slots

The Slot component can be used multiple times in the same component, as long as it has a different name property:

```
import { Slot, component$, useStylesScoped$ } from '@builder.io/qwik';
import CSS from './index.css?inline';
 
const Tab = component$(() => {
  useStylesScoped$(CSS);
  return (
    <section>
      <h2>
        <Slot name="title" />
      </h2>
      <div>
        <Slot /> {/* default slot */}
        <div>
          <Slot name="footer" />
        </div>
      </div>
    </section>
  );
});
 
export default component$(() => {
  return (
    <Tab>
      <div q:slot="title">Qwik</div>
      <div>A resumable framework for building instant web applications</div>
      <span q:slot="footer">made with ❤️ by </span>
      <a q:slot="footer" href="https://builder.io">
        builder.io
      </a>
    </Tab>
  );
});
```

Now, when consuming the <Tab> component, we can pass children and specify in which slot they should be placed, using the q:slot attribute:

Notice that:

### Unprojected Content

Qwik keeps all content around, even if not projected. This is because the content could be projected in the future. When projected content does not match any <Slot> component, the content is moved into an inert <q:template> element.

```
import { Slot, component$, useSignal } from '@builder.io/qwik';
 
const Accordion = component$(() => {
  const isOpen = useSignal(false);
  return (
    <div>
      <h1 onClick$={() => (isOpen.value = !isOpen.value)}>
        {isOpen.value ? '▼' : '▶︎'}
      </h1>
      {isOpen.value && <Slot />}
    </div>
  );
});
 
export default component$(() => {
  return (
    <Accordion>
      I am pre-rendered on the Server and hidden until needed.
    </Accordion>
  );
});
```

Results in:

```
<div>
  <h1>▶︎</h1>
</div>
<q:template q:slot hidden aria-hidden="true">
  I am pre-rendered on the Server and hidden until needed.
</q:template>
```

Notice that the un-projected content is moved into an inert <q:template>. This is done in case the Accordion component re-renders in the <Slot>. In this case, we avoid having to re-render the parent component just to generate the projected content. By persisting the un-projected content when the parent is initially rendered, the rendering of the two components can stay independent.

### Invalid Projection

The q:slot attribute must be a direct child of a component.

```
import { component$ } from '@builder.io/qwik';
 
export const Project = component$(() => { ... })
 
export const MyApp = component$(() => {
  return (
    <Project>
      <span q:slot="title">ok, direct child of Project</span>
      <div>
        <span q:slot="title">Error, not a direct child of Project</span>
      </div>
    </Project>
  );
});
```

## Advanced Example

An example of a collapsible component that conditionally projects editable content.

```
import { Slot, component$, useSignal } from '@builder.io/qwik';
 
export const Collapsible = component$(() => {
  const isOpen = useSignal(true);
 
  return (
    <div>
      <h1 onClick$={() => (isOpen.value = !isOpen.value)}>
        {isOpen.value ? '▼' : '▶︎'}
        <Slot name="title" />
      </h1>
      {isOpen.value && <Slot />}
    </div>
  );
});
 
export default component$(() => {
  const title = useSignal('Qwik');
  const description = useSignal(
    'A resumable framework for building instant web applications'
  );
  return (
    <>
      <label>Title</label>
      <input bind:value={title} type="text" />
      <label>Description</label>
      <textarea bind:value={description} cols={50} />
      <hr />
      <Collapsible>
        <span q:slot="title">{title}</span>
        {description}
      </Collapsible>
    </>
  );
});
```

The Collapsible component will always display the title, but the body of the text will only display if store.isOpen is true.

Additionally, the title and description of the projected content are editable.

In order for the two components to have an independent lifecycle, the projection needs to be declarative. In this way, either the parent or child can change what is projected or how it is projected without forcing the re-rendering of the other.

### Projection vs children

All frameworks need a way for a component to wrap its complex content conditionally. This problem is solved in many different ways, but there are two predominant approaches:

The two approaches can best be described as declarative vs imperative. They both come with their set of advantages and disadvantages.

Qwik uses the declarative projection approach because it needs to be able to render parent and child components independently from each other. In an imperative  approach, there are countless ways a child component can modify the children. If a child component relied on its children, it would be forced to re-render every time the parent component re-rendered to reapply the changes. This additional rendering contradicts Qwik's goal of having components render in isolation.

Note: Make sure to use <Slot /> within a component$() function to ensure it works correctly. <Slot /> cannot operate in inline components which are similar to normal functions export const MyInlineComp = () => .

### Advanced: Slots and Context

Slotted components have access to the Context of their parent component, even while they aren't being projected. Furthermore, if the parent is projecting the <Slot /> inside another component, the slotted components will also have access to the Contexts of that deeper component.

However, if a component hasn't been projected yet because the <Slot /> are rendered conditionally, it's impossible to know about the deeper Context, and then the slotted component will only see the Context of the immediate parent.

As such, it's safest to avoid these situations; if you are providing Contexts, don't conditionally render your <Slot />.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
