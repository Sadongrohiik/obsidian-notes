# https://qwik.dev/docs/getting-started/

[Original link](https://qwik.dev/docs/getting-started/)

# Getting Started Qwikly

Qwik is a new kind of framework that is resumable (no eager JS execution and no hydration), built for the edge and familiar to React developers.

To play with it right away, check out Qwik’s in-browser playgrounds:

## Prerequisites

To get started with Qwik locally, you need the following:

## Create an app using the CLI

First, use the Qwik CLI to generate a blank starter application, to quickly familiarize yourself with it.  The same command can be used to create projects for either Qwik or Qwik city.

Run the Qwik CLI in your shell. Qwik supports pnpm, npm, yarn and bun. Choose the package manager you prefer and run one of the following commands:

```
pnpm create qwik@latest
```

```
npm create qwik@latest
```

```
yarn create qwik
```

```
bun create qwik@latest
```

The CLI guides you through an interactive menu to set the project-name, select one of the starters, and ask if you want to install the dependencies.  To find out more about the files generated, refer to the Project Structure documentation.

Start the development server:

```
pnpm run start
```

```
npm run start
```

```
yarn run start
```

```
bun run start
```

## Qwik Joke App

The Qwik Hello World tutorial guides you through building a joke app with Qwik while covering the most important Qwik concepts. The app displays a random joke from https://icanhazdadjoke.com and features a button to get a new joke on click.

### 1. Create A Route

Start by serving a page at a particular route. This basic app serves a random dad joke application on the /joke/ route. This tutorial relies on Qwikcity, Qwik's meta-framework, which uses directory-based routing. To get started:

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return <section class="section bright">A Joke!</section>;
});
```

NOTE:

### 2. Loading Data

Use the external JSON API at https://icanhazdadjoke.com to load random jokes. You can use route loaders to load this data into the server and render it in the component.

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useDadJoke = routeLoader$(async () => {
  const response = await fetch('https://icanhazdadjoke.com/', {
    headers: { Accept: 'application/json' },
  });
  return (await response.json()) as {
    id: string;
    status: number;
    joke: string;
  };
});
 
export default component$(() => {
  // Calling our `useDadJoke` hook, will return a reactive signal to the loaded data.
  const dadJokeSignal = useDadJoke();
  return (
    <section class="section bright">
      <p>{dadJokeSignal.value.joke}</p>
    </section>
  );
});
```

Code explanation:

NOTE

### 3. Posting Data to the Server

Previously, the component routeLoader$ was used to send data from the server to the client. To post (send) data from the client back to the server, use routeAction$.

NOTE: routeAction$ is the preferred way to send data to the server because it uses the browser native form API, which works even if JavaScript is disabled.

To declare an action, add this code:

```
import { routeLoader$, Form, routeAction$ } from '@builder.io/qwik-city';
 
export const useJokeVoteAction = routeAction$((props) => {
  // Leave it as an exercise for the reader to implement this.
  console.log('VOTE', props);
});
```

```
export default component$(() => {
  const dadJokeSignal = useDadJoke();
  const favoriteJokeAction = useJokeVoteAction();
  return (
    <section class="section bright">
      <p>{dadJokeSignal.value.joke}</p>
      <Form action={favoriteJokeAction}>
        <input type="hidden" name="jokeID" value={dadJokeSignal.value.id} />
        <button name="vote" value="up">👍</button>
        <button name="vote" value="down">👎</button>
      </Form>
    </section>
  );
});
```

Code explanation:

Things to note:

For reference, the complete code snippet for this section is as follows:

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$, Form, routeAction$ } from '@builder.io/qwik-city';
 
export const useDadJoke = routeLoader$(async () => {
  const response = await fetch('https://icanhazdadjoke.com/', {
    headers: { Accept: 'application/json' },
  });
  return (await response.json()) as {
    id: string;
    status: number;
    joke: string;
  };
});
 
export const useJokeVoteAction = routeAction$((props) => {
  console.log('VOTE', props);
});
 
export default component$(() => {
  // Calling our `useDadJoke` hook, will return a reactive signal to the loaded data.
  const dadJokeSignal = useDadJoke();
  const favoriteJokeAction = useJokeVoteAction();
  return (
    <section class="section bright">
      <p>{dadJokeSignal.value.joke}</p>
      <Form action={favoriteJokeAction}>
        <input type="hidden" name="jokeID" value={dadJokeSignal.value.id} />
        <button name="vote" value="up">
          👍
        </button>
        <button name="vote" value="down">
          👎
        </button>
      </Form>
    </section>
  );
});
```

### 4. Modifying State

Keeping track of the state and updating the UI is core to what applications do. Qwik provides a useSignal hook to keep track of the application's state. To learn more, see state management.

To declare state:

```
import { component$, useSignal } from "@builder.io/qwik";
```

```
const isFavoriteSignal = useSignal(false);
```

```
<button
 onClick$={() => {
   isFavoriteSignal.value = !isFavoriteSignal.value;
 }}>
  {isFavoriteSignal.value ? '❤️' : '🤍'}
</button>
```

NOTE: Clicking on the button updates the state, which in turn updates the UI.

For reference, the complete code snippet for this section is as follows:

```
import { component$, useSignal } from '@builder.io/qwik';
import { routeLoader$, Form, routeAction$ } from '@builder.io/qwik-city';
 
export const useDadJoke = routeLoader$(async () => {
  const response = await fetch('https://icanhazdadjoke.com/', {
    headers: { Accept: 'application/json' },
  });
  return (await response.json()) as {
    id: string;
    status: number;
    joke: string;
  };
});
 
export const useJokeVoteAction = routeAction$((props) => {
  console.log('VOTE', props);
});
 
export default component$(() => {
  const isFavoriteSignal = useSignal(false);
  // Calling our `useDadJoke` hook, will return a reactive signal to the loaded data.
  const dadJokeSignal = useDadJoke();
  const favoriteJokeAction = useJokeVoteAction();
 
  return (
    <section class="section bright">
      <p>{dadJokeSignal.value.joke}</p>
      <Form action={favoriteJokeAction}>
        <input type="hidden" name="jokeID" value={dadJokeSignal.value.id} />
        <button name="vote" value="up">
          👍
        </button>
        <button name="vote" value="down">
          👎
        </button>
      </Form>
      <button
        onClick$={() => (isFavoriteSignal.value = !isFavoriteSignal.value)}
      >
        {isFavoriteSignal.value ? '❤️' : '🤍'}
      </button>
    </section>
  );
});
```

### 5. Tasks and Invoking Server Code

In Qwik, a task is work that needs to happen when a state changes. (This is similar to an "effect" in other frameworks.) In this example, we use the task to invoke code on the server.

Import useTask$ from qwik and server$ from qwik-city.

```
import { component$, useSignal, useTask$ } from "@builder.io/qwik";
import {
  routeLoader$,
  Form,
  routeAction$,
  server$,
} from '@builder.io/qwik-city';
```

Create a new task that tracks the isFavoriteSignal state:

```
useTask$(({ track }) => {});
```

Add a track call to re-execute the task on isFavoriteSignal state change:

```
useTask$(({ track }) => {
  track(() => isFavoriteSignal.value);
});
```

Add the work that you want to execute on state change:

```
useTask$(({ track }) => {
  track(() => isFavoriteSignal.value);
  console.log('FAVORITE (isomorphic)', isFavoriteSignal.value);
});
```

If you want to have work happen on the server only, wrap it in server$()

```
useTask$(({ track }) => {
  track(() => isFavoriteSignal.value);
  console.log('FAVORITE (isomorphic)', isFavoriteSignal.value);
  server$(() => {
    console.log('FAVORITE (server)', isFavoriteSignal.value);
  })();
});
```

NOTE:

For reference, the complete code snippet for this section is as follows:

```
import { component$, useSignal, useTask$ } from '@builder.io/qwik';
import {
  routeLoader$,
  Form,
  routeAction$,
  server$,
} from '@builder.io/qwik-city';
 
export const useDadJoke = routeLoader$(async () => {
  const response = await fetch('https://icanhazdadjoke.com/', {
    headers: { Accept: 'application/json' },
  });
  return (await response.json()) as {
    id: string;
    status: number;
    joke: string;
  };
});
 
export const useJokeVoteAction = routeAction$((props) => {
  console.log('VOTE', props);
});
 
export default component$(() => {
  const isFavoriteSignal = useSignal(false);
  // Calling our `useDadJoke` hook, will return a reactive signal to the loaded data.
  const dadJokeSignal = useDadJoke();
  const favoriteJokeAction = useJokeVoteAction();
  useTask$(({ track }) => {
    track(() => isFavoriteSignal.value);
    console.log('FAVORITE (isomorphic)', isFavoriteSignal.value);
    server$(() => {
      console.log('FAVORITE (server)', isFavoriteSignal.value);
    })();
  });
  return (
    <section class="section bright">
      <p>{dadJokeSignal.value.joke}</p>
      <Form action={favoriteJokeAction}>
        <input type="hidden" name="jokeID" value={dadJokeSignal.value.id} />
        <button name="vote" value="up">
          👍
        </button>
        <button name="vote" value="down">
          👎
        </button>
      </Form>
      <button
        onClick$={() => (isFavoriteSignal.value = !isFavoriteSignal.value)}
      >
        {isFavoriteSignal.value ? '❤️' : '🤍'}
      </button>
    </section>
  );
});
```

### 6. Styling

Styling is an important part of any application. Qwik provides a way to associate and scope styles with your component.

To add styles:

Create a new file src/routes/joke/index.css:

```
p {
  font-weight: bold;
}
 
form {
  float: right;
}
```

import the styles in src/routes/joke/index.tsx:

```
import styles from "./index.css?inline";
```

Import useStylesScoped$ from qwik.

```
import { component$, useSignal, useStylesScoped$, useTask$ } from "@builder.io/qwik";
```

Tell the component to load the styles:

```
useStylesScoped$(styles);
```

Code explanation:

For reference, the complete code snippet for this section is as follows:

```
import {
  component$,
  useSignal,
  useStylesScoped$,
  useTask$,
} from '@builder.io/qwik';
import {
  routeLoader$,
  Form,
  routeAction$,
  server$,
} from '@builder.io/qwik-city';
import styles from './index.css?inline';
 
export const useDadJoke = routeLoader$(async () => {
  const response = await fetch('https://icanhazdadjoke.com/', {
    headers: { Accept: 'application/json' },
  });
  return (await response.json()) as {
    id: string;
    status: number;
    joke: string;
  };
});
 
export const useJokeVoteAction = routeAction$((props) => {
  console.log('VOTE', props);
});
 
export default component$(() => {
  useStylesScoped$(styles);
  const isFavoriteSignal = useSignal(false);
  // Calling our `useDadJoke` hook, will return a reactive signal to the loaded data.
  const dadJokeSignal = useDadJoke();
  const favoriteJokeAction = useJokeVoteAction();
  useTask$(({ track }) => {
    track(() => isFavoriteSignal.value);
    console.log('FAVORITE (isomorphic)', isFavoriteSignal.value);
    server$(() => {
      console.log('FAVORITE (server)', isFavoriteSignal.value);
    })();
  });
  return (
    <section class="section bright">
      <p>{dadJokeSignal.value.joke}</p>
      <Form action={favoriteJokeAction}>
        <input type="hidden" name="jokeID" value={dadJokeSignal.value.id} />
        <button name="vote" value="up">👍</button>
        <button name="vote" value="down">👎</button>
      </Form>
      <button
        onClick$={() => (isFavoriteSignal.value = !isFavoriteSignal.value)}
      >
        {isFavoriteSignal.value ? '❤️' : '🤍'}
      </button>
    </section>
  );
});
```

### 7. Preview

Up until now, you've been using the dev server to make your application.

This is great to see your changes in real time, but it doesn't work the same way as in production:

To make sure everything is ready for production and eliminate these issues, you can run your app in preview:

```
pnpm run preview
```

```
npm run preview
```

```
yarn run preview
```

```
bun run preview
```

NOTE:

## Review

Congratulations, you've learned a lot about Qwik!
For more on just how much you can achieve with Qwik, check out the dedicated docs on each of the topics touched on in this tutorial:

### Contributors

Thanks to all the contributors who have helped make this documentation better!
