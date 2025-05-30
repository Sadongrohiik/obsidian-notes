# https://qwik.dev/docs/integrations/react/

[Original link](https://qwik.dev/docs/integrations/react/)

# Qwik React ⚛️

Qwik React allows you to use React within Qwik. The advantage of using Qwik React is that you can use existing React components and libraries within Qwik. This allows you to take advantage of the large ecosystem of React components and libraries such as Material UI, Threejs and React Spring. It is also a good way to get the benefits of Qwik without having to rewrite your React application.

## Basic Usage

The basic usage of Qwik React is to take existing React components and wrap them in a qwikify$ function. This function will create a Qwik component that can be used within Qwik and which will turn the React component into an island allowing you the freedom to fine-tune when the React component should hydrate.

Basic usage

```
// This pragma is required so that React JSX is used instead of Qwik JSX
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
 
// An existing React component
function Greetings() {
  return <div>Hello from React</div>;
}
 
// Qwik component wrapping the React component
export const QGreetings = qwikify$(Greetings);
```

## 0. Installation

Before you can use Qwik React you need to configure the Qwik project to use Qwik React. The simplest way is to run the following command:

If you don't have a Qwik app yet, then you need to create one first, then, follow the instructions and run the command add React to your app.

```
pnpm run qwik add react
```

```
npm run qwik add react
```

```
yarn run qwik add react
```

```
bun run qwik add react
```

The above command will perform the following:

```
{
 ...,
  "dependencies": {
   ...,
    "@builder.io/qwik-react": "0.5.0",
    "@types/react": "18.0.28",
    "@types/react-dom": "18.0.11",
    "react": "18.2.0",
    "react-dom": "18.2.0",
  }
}
```

Note: This is not an emulation of React. We are using the actual React library.

```
// vite.config.ts
import { qwikReact } from '@builder.io/qwik-react/vite';
 
export default defineConfig(() => {
   return {
     ...,
     plugins: [
       ...,
       // The important part
       qwikReact()
     ],
   };
});
```

Note: The qwik add react command will also configure a demo route showcasing the Qwik React integration. These are:

We will ignore these in this guide and instead take you through the process from the beginning.

## 1. Hello World

Let's start with a simple example. We will create a simple React component and then wrap it in a Qwik component. We will then use the Qwik component in a Qwik route.

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
 
// Create React component standard way
function Greetings() {
  return <p>Hello from React</p>;
}
 
// Convert React component to Qwik component
export const QGreetings = qwikify$(Greetings);
```

```
import { component$ } from '@builder.io/qwik';
import { QGreetings } from './react';
 
export default component$(() => {
  return (
    <main>
      <p>Hello from Qwik</p>
      <QGreetings />
    </main>
  );
});
```

The @builder.io/qwik-react package exports the qwikify$() function that lets you convert React components into Qwik components, that you can use across your application.

Note: You CAN NOT use React components in Qwik without converting them first, using qwikify$(). Even though React and Qwik components look similar, they are fundamentally very different.

React and Qwik components can not be mixed in the same file, if you check your project right after running the installation command, you will see a new folder src/integrations/react/, we recommend that you place your React components there.

## 2. Hydrating react islands

The above example shows how to SSR static React content on the server. The benefit is that that component will never re-render in the browser and therefore its code never downloads to the client. But what if the component needs to be interactive, and therefore we need to download its behavior in the browser? Let's start with building a simple counter example in React.

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
import { useState } from 'react';
 
// Create React component standard way
function Counter() {
  const [count, setCount] = useState(0);
  return (
    <button className="react" onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
 
// Convert React component to Qwik component
export const QCounter = qwikify$(Counter);
```

```
import { component$ } from '@builder.io/qwik';
import { QCounter } from './react';
 
export default component$(() => {
  return (
    <main>
      <QCounter />
    </main>
  );
});
```

Notice that clicking on the Count button does nothing. This is because the React has not been downloaded and therefore the component was not hydrated. We need to tell Qwik to download the React component and hydrate it, but we need to specify the condition under which we want to do that. Doing it eagerly would lose all of the benefits of turning the React application into islands. In this case, we want to download the component when the user hovers over the button, we do so by adding {: eagerness: 'hover' } to qwikify$().

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
import { useState } from 'react';
 
// Create React component standard way
function Counter() {
  // Print to console to show when the component is rendered.
  console.log('React <Counter/> Render');
  const [count, setCount] = useState(0);
  return (
    <button className="react" onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
 
// Specify eagerness to hydrate component on hover event.
export const QCounter = qwikify$(Counter, { eagerness: 'hover' });
```

```
import { component$ } from '@builder.io/qwik';
import { QCounter } from './react';
 
export default component$(() => {
  console.log('Qwik Render');
  return (
    <main>
      <QCounter />
    </main>
  );
});
```

In this example, we have brought up the console to show what is going on behind the scene. When you hover over the button, you will see that the React component is rendered. This is because we asked Qwik to hydrate the component on hover. Now that the component is hydrated you can interact with it and it will correctly update the count.

By giving the eagerness property to qwikify$(), we are allowing you to fine-tune the conditions under which the component is hydrated which will impact the startup performance of your application.

## 3. Inter-island communication

In the previous example, we had a single island that we delay-hydrated. But once you have multiple islands, there will be a need to communicate between them. This example shows how to do inter-island communication with Qwik.

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
 
function Button({ onClick }: { onClick: () => void }) {
  console.log('React <Button/> Render');
  return <button onClick={onClick}>+1</button>;
}
 
function Display({ count }: { count: number }) {
  console.log('React <Display count=' + count + '/> Render');
  return <p className="react">Count: {count}</p>;
}
 
export const QButton = qwikify$(Button, { eagerness: 'hover' });
export const QDisplay = qwikify$(Display);
```

```
import { component$, useSignal } from '@builder.io/qwik';
import { QButton, QDisplay } from './react';
 
export default component$(() => {
  console.log('Qwik Render');
  const count = useSignal(0);
  return (
    <main>
      <QButton
        onClick$={() => {
          console.log('click', count.value);
          count.value++;
        }}
      />
      <QDisplay count={count.value}></QDisplay>
    </main>
  );
});
```

In the above example, we have two islands, one for the button (QButton) and one for the display (QDisplay). The button island is hydrated on hover and the display island is not hydrated on any event.

The react.tsx file has:

The index.tsx file has:

When you hover over the button, you will see that the QButton island is hydrated. When you click the button, you will see that the QDisplay island is hydrated and the count is updated. (The double execution of QDisplay is due to initial hydration first, and then updating the count second.)

Notice that Qwik React only needs to eagerly hydrate components that have interactivity. Components that are dynamic, but don't have interactivity (such as QDisplay in this example) do not need to be eagerly hydrated instead they hydrate automatically when their props change.

Also notice that console.log('Qwik Render'); never executes in the browser.

## 4. host: Listeners

In the previous example, we had two islands. The QButton had to be eagerly hydrated so that React can set up the onClick event handler. This is a bit wasteful because the QButton island will never need to be re-rendered as its output is static. Clicking on the QButton will not cause the QButton island to re-render. In such a case, we can ask Qwik to register the click listener instead of hydrating the whole component in React just to attach a listener. This is done by using the host: prefix in the event name.

```
import { component$, useSignal } from '@builder.io/qwik';
import { QButton, QDisplay } from './react';
 
export default component$(() => {
  console.log('Qwik Render');
  const count = useSignal(0);
  return (
    <main>
      <QButton
        host:onClick$={() => {
          console.log('click', count.value);
          count.value++;
        }}
      >
        +1
      </QButton>
      <QDisplay count={count.value}></QDisplay>
    </main>
  );
});
```

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
import { type ReactNode } from 'react';
 
function Button({ children }: { children?: ReactNode[] }) {
  console.log('React <Button/> Render');
  return <button>{children}</button>;
}
 
function Display({ count }: { count: number }) {
  console.log('React <Display count=' + count + '/> Render');
  return <div className="react">Count: {count}</div>;
}
 
export const QButton = qwikify$(Button);
export const QDisplay = qwikify$(Display);
```

Now hovering over the button will not do anything (no React hydration). Clicking on the button will cause Qwik to handle the event and update the signal which will in turn cause the hydration of the QDisplay island. Notice that the QButton island is never hydrated. Therefore this change allowed us to have an island that renders server side only and never needs to be hydrated in the browser, saving our user time.

## 5. Projecting children

A common use case is to pass content children to components. This works with Qwik React as well. In the React component just declare children in your props and use them as expected (See react.tsx).

```
import { component$, useSignal } from '@builder.io/qwik';
import { QFrame } from './react';
 
export default component$(() => {
  console.log('Qwik Render');
  const count = useSignal(0);
  return (
    <QFrame>
      <button
        onClick$={() => {
          console.log('click', count.value);
          count.value++;
        }}
      >
        +1
      </button>
      Count: {count}
    </QFrame>
  );
});
```

```
/** @jsxImportSource react */
import { type ReactNode } from 'react';
import { qwikify$ } from '@builder.io/qwik-react';
 
function Frame({ children }: { children?: ReactNode[] }) {
  console.log('React <Zippy/> Render');
  return (
    <div
      style={{
        display: 'inline-block',
        border: '1px solid black',
        borderRadius: '10px',
        padding: '5px',
      }}
    >
      {children}
    </div>
  );
}
 
export const QFrame = qwikify$(Frame);
```

Notice that the QFrame island is never hydrated because it has no eagerness or any props which would trigger hydration. But also notice that the children do re-render when the signal changes and are correctly projected into the React QFrame island without the island being hydrated. This allows even more of the page to be rendered server-side and never rendered on the client.

## 6. Using React libraries

Finally, it is possible to use React libraries in your Qwik application. In this example Material UI and Emotion are used to render this React example.

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
import Tabs from '@mui/material/Tabs';
import Tab from '@mui/material/Tab';
import Box from '@mui/material/Box';
import { type ReactNode } from 'react';
 
export const Example = qwikify$(
  function Example({
    selected,
    onSelected,
    children,
  }: {
    selected: number;
    onSelected: (v: number) => any;
    children?: ReactNode[];
  }) {
    console.log('React <Example/> Render');
    return (
      <>
        <Box sx={{ borderBottom: 1, borderColor: 'divider' }}>
          <Tabs
            value={selected}
            onChange={(e, v) => onSelected(v)}
            aria-label="basic tabs example"
          >
            <Tab label="Item One" />
            <Tab label="Item Two" />
            <Tab label="Item Three" />
          </Tabs>
          {children}
        </Box>
      </>
    );
  },
  { eagerness: 'hover' }
);
```

```
import { component$, useSignal } from '@builder.io/qwik';
import { Example } from './react';
 
export default component$(() => {
  console.log('Qwik Render');
  const selected = useSignal(0);
  return (
    <Example
      selected={selected.value}
      onSelected$={(v) => (selected.value = v)}
    >
      Selected tab: {selected.value}
    </Example>
  );
});
```

The React example is hydrated on hover and works as you would expect.

# Rules

Let's look at this example to better understand the rules of Qwik React.

```
/** @jsxImportSource react */
 
import { qwikify$ } from '@builder.io/qwik-react';
import { Alert, Button, Slider } from '@mui/material';
import { DataGrid, GridColDef, GridValueGetterParams } from '@mui/x-data-grid';
 
export const MUIButton = qwikify$(Button);
export const MUIAlert = qwikify$(Alert);
export const MUISlider = qwikify$(Slider, { eagerness: 'hover' });
```

Important: You need to import /** @jsxImportSource react */ at the top of your file, this is an instruction to the compiler to use React as the JSX factory.

In a nutshell, the rules are:

Now your Qwik can import MUIButton and use it as any other Qwik component:

```
import { component$ } from '@builder.io/qwik';
import { MUIAlert, MUIButton } from '~/integrations/react/mui';
 
export default component$(() => {
  return (
    <>
      <MUIButton client:hover>Hello this is a button</MUIButton>
 
      <MUIAlert severity="warning">This is a warning from Qwik</MUIAlert>
    </>
  );
});
```

## qwikify$()

The qwikify$(ReactCmp, options?): QwikCmp allows to implement partial hydration of React components. It works by wrapping the SSR and hydration logic of React into a Qwik component that can execute React's renderToString() during SSR and dynamically call hydrateRoot() when specified.

Notice that by default no React code will run in the browser, meaning that React component will NOT be interactive by default, for example, in the following example, we qwikify the Slider component from MUI, but it will not be interactive (it is missing an eagerness property to tell Qwik when the React component should be hydrated in the browser.)

```
/** @jsxImportSource react */
import { qwikify$ } from '@builder.io/qwik-react';
import { Slider } from '@mui/material';
export const MUISlider = qwikify$<typeof Slider>(
  Slider
  //  Uncomment next line to make component interactive in browser
  // { eagerness: 'hover' }
);
```

```
import { component$, useSignal } from '@builder.io/qwik';
import { QFrame } from './react';
 
export default component$(() => {
  console.log('Qwik Render');
  const count = useSignal(0);
  return (
    <QFrame>
      <button
        onClick$={() => {
          console.log('click', count.value);
          count.value++;
        }}
      >
        +1
      </button>
      Count: {count}
    </QFrame>
  );
});
```

## Limitations

### Every qwikified react component is isolated

Each instance of a qwikified react component becomes an independent React app. Fully isolated.

```
export const MUISlider = qwikify$(Slider);
 
<MUISlider></MUISlider>
<MUISlider></MUISlider>
```

### By default interactivity is disabled

By default, qwikified components will not be interactive, please look at the next section to learn how to enable interactivity.

### Use qwikify$() as a migration strategy

Using React components in Qwik is a great way to migrate your application to Qwik, but it's not a silver bullet, you will need to rewrite your components to take advantage of Qwik's features.

It's also a great way to enjoy the React ecosystem, like threejs or data-grid libs.

Don't abuse qwikify$() to build your application, as overusing will cause performance gains to be lost.

### Build wide islands, not leaf nodes

For example, if you need to use several MUI components, to build a list, don't qwikify each individual MUI component, instead, build the whole list as a single qwikified React component.

#### GOOD: Wide island

A single qwikified component, with all the MUI components inside. Styles will not be duplicated, and context and theming will work as expected.

```
import * as React from 'react';
import List from '@mui/material/List';
import ListItem from '@mui/material/ListItem';
import ListItemText from '@mui/material/ListItemText';
import ListItemAvatar from '@mui/material/ListItemAvatar';
import Avatar from '@mui/material/Avatar';
import ImageIcon from '@mui/icons-material/Image';
import WorkIcon from '@mui/icons-material/Work';
import BeachAccessIcon from '@mui/icons-material/BeachAccess';
 
// Qwikify the whole list
export const FolderList = qwikify$(() => {
  return (
    <List sx={{ width: '100%', maxWidth: 360, bgcolor: 'background.paper' }}>
      <ListItem>
        <ListItemAvatar>
          <Avatar>
            <ImageIcon />
          </Avatar>
        </ListItemAvatar>
        <ListItemText primary="Photos" secondary="Jan 9, 2014" />
      </ListItem>
      <ListItem>
        <ListItemAvatar>
          <Avatar>
            <WorkIcon />
          </Avatar>
        </ListItemAvatar>
        <ListItemText primary="Work" secondary="Jan 7, 2014" />
      </ListItem>
      <ListItem>
        <ListItemAvatar>
          <Avatar>
            <BeachAccessIcon />
          </Avatar>
        </ListItemAvatar>
        <ListItemText primary="Vacation" secondary="July 20, 2014" />
      </ListItem>
    </List>
  );
});
```

#### BAD: Leaf nodes

Leaf nodes are qwikified independently, effectively rendering dozens of nested react applications, each fully isolated from the others, and styles being duplicated.

```
import * as React from 'react';
import List from '@mui/material/List';
import ListItem from '@mui/material/ListItem';
import ListItemText from '@mui/material/ListItemText';
import ListItemAvatar from '@mui/material/ListItemAvatar';
import Avatar from '@mui/material/Avatar';
import ImageIcon from '@mui/icons-material/Image';
import WorkIcon from '@mui/icons-material/Work';
import BeachAccessIcon from '@mui/icons-material/BeachAccess';
 
export const MUIList = qwikify$(List);
export const MUIListItem = qwikify$(ListItem);
export const MUIListItemText = qwikify$(ListItemText);
export const MUIListItemAvatar = qwikify$(ListItemAvatar);
export const MUIAvatar = qwikify$(Avatar);
export const MUIImageIcon = qwikify$(ImageIcon);
export const MUIWorkIcon = qwikify$(WorkIcon);
export const MUIBeachAccessIcon = qwikify$(BeachAccessIcon);
```

```
// Qwik component using dozens of nested React islands
// Each MUI-* it's an independent React application
export const FolderList = component$(() => {
  return (
    <MUIList sx={{ width: '100%', maxWidth: 360, bgcolor: 'background.paper' }}>
      <MUIListItem>
        <MUIListItemAvatar>
          <MUIAvatar>
            <MUIImageIcon />
          </MUIAvatar>
        </MUIListItemAvatar>
        <MUIListItemText primary="Photos" secondary="Jan 9, 2014" />
      </MUIListItem>
      <MUIListItem>
        <MUIListItemAvatar>
          <MUIAvatar>
            <MUIWorkIcon />
          </MUIAvatar>
        </MUIListItemAvatar>
        <MUIListItemText primary="Work" secondary="Jan 7, 2014" />
      </MUIListItem>
      <MUIListItem>
        <MUIListItemAvatar>
          <MUIAvatar>
            <MUIBeachAccessIcon />
          </MUIAvatar>
        </MUIListItemAvatar>
        <MUIListItemText primary="Vacation" secondary="July 20, 2014" />
      </MUIListItem>
    </MUIList>
  );
});
```

## Adding interactivity

In order to add interactivity, in React terminology we need to hydrate, usually in React applications this hydration task happens unconditionally at load time, adding a massive overhead and making sites slow.

Qwik allows you decide when to hydrate your components, by using the client: JSX properties, this technique is commonly called partial hydration, popularized by Astro.

```
export default component$(() => {
  return (
    <>
-      <MUISlider></MUISlider>
+      <MUISlider client:visible></MUISlider>
    </>
  );
});
```

Qwik comes with different strategies out of the box:

### client:load

The component eagerly hydrates when the document loads.

```
<MUISlider client:load></MUISlider>
```

Use case: Immediately-visible UI elements that need to be interactive as soon as possible.

### client:idle

The component eagerly hydrates when the browser first becomes idle, ie, when everything important has already run before.

```
<MUISlider client:idle></MUISlider>
```

Use case: Lower-priority UI elements that don’t need to be immediately interactive.

### client:visible

The component eagerly hydrates when it becomes visible in the viewport.

```
<MUISlider client:visible></MUISlider>
```

Use case: Low-priority UI elements that are either far down the page (“below the fold”) or so resource-intensive to load that you would prefer not to load them at all if the user never saw the element.

### client:hover

The component eagerly hydrates when the mouse is over the component.

```
<MUISlider client:hover></MUISlider>
```

Use case: Lowest-priority UI elements which interactivity is not crucial, and only needs to run in desktop.

### client:signal

This is an advanced API that allows to hydrate the component whenever the passed signal becomes true.

```
export default component$(() => {
  const hydrateReact = useSignal(false);
  return (
    <>
      <button onClick$={() => (hydrateReact.value = true)}>Hydrate Slider when click</button>
 
      <MUISlider client:signal={hydrateReact}></MUISlider>
    </>
  );
});
```

This effectively allows you to implement custom strategies for hydration.

### client:event

The component eagerly hydrates when specified DOM events are dispatched.

```
<MUISlider client:event="click"></MUISlider>
```

### client:only

When true, the component will not run in SSR, only in the browser.

```
<MUISlider client:only></MUISlider>
```

## Listening to React events

Events in React are handled by passing a function as a property to the component, for example:

```
// React code (won't work in Qwik)
 
import { Slider } from '@mui/material';
 
<Slider onChange={() => console.log('value changed')}></Slider>;
```

The qwikify() function will convert this into a Qwik component that will also expose the React events as Qwik QRLs:

```
import { Slider } from '@mui/material';
import { qwikify$ } from '@builder.io/qwik-react';
const MUISlider = qwikify$(Slider);
 
<MUISlider client:visible onChange$={() => console.log('value changed')} />;
```

Notice that we use the client:visible property to eagerly hydrate the component, otherwise the component would not be interactive and the events would never be dispatched.

## Host element

When wrapping a React component with qwikify$(), under the hood, a new DOM element is created, such as:

```
<qwik-react>
  <button class="MUI-button"></button>
</qwik-react>
```

Notice, that the tag name of the wrapper element is configurable via tagName: qwikify$(ReactCmp, { tagName: 'my-react' }).

### Listen to DOM events without hydration

The host element is not part of React, meaning that hydration is not necessary to listen for events, in order to add custom attributes and events to the host element, you can use the host: prefix in the JSX properties, such as:

```
<MUIButton
  host:onClick$={() => {
    console.log('click a react component without hydration!!');
  }}
/>
```

This will effectively allow you to respond to a click in a MUI button without downloading a single byte of React code.

🧑‍💻Happy hacking!

### Contributors

Thanks to all the contributors who have helped make this documentation better!
