# https://qwik.dev/docs/advanced/eslint/

[Original link](https://qwik.dev/docs/advanced/eslint/)

# ESLint-Rules

Qwik comes with its own set of ESLint rules to help developers write better code.

✅
Warn in 'recommended' ruleset

✅
Error in 'recommended' ruleset

🔔
Warn in 'strict' ruleset

🔔
Error in 'strict' ruleset

## Possible Problems

These rules are available.

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

✅

🔔

## Details

### use-method-usage

#### useWrongFunction

Examples of correct code for this rule:

```
export const Counter = component$(() => {
  const count = useSignal(0);
});
```

```
export const useCounter = () => {
  const count = useSignal(0);
  return count;
};
```

Examples of incorrect code for this rule:

```
export const Counter = (() => {
  const count = useSignal(0);
});
```

use* methods can only be used in component$ functions or inside use* hooks (e.g. useCounter).

### valid-lexical-scope

#### referencesOutside

Examples of correct code for this rule:

```
import { component$, useTask$, $ } from '@builder.io/qwik';
 
export const HelloWorld = component$(() => {
  const print = $((msg: string) => {
    console.log(msg);
  });
 
  useTask$(() => {
    print("Hello World");
  });
 
  return <h1>Hello</h1>;
});
```

Examples of incorrect code for this rule:

```
import { component$, useTask$ } from '@builder.io/qwik';
 
export const HelloWorld = component$(() => {
  const print = (msg: string) => {
    console.log(msg);
  };
 
  useTask$(() => {
    print("Hello World");
  });
 
  return <h1>Hello</h1>;
});
```

Since Expressions are not serializable, they must be wrapped with $( ... ) so that the optimizer can split the code into small chunks.

#### invalidJsxDollar

Examples of correct code for this rule:

```
import { component$, $ } from '@builder.io/qwik';
 
export const HelloWorld = component$(() => {
  const click = $(() => console.log());
  return (
    <button onClick$={click}>log it</button>
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const HelloWorld = component$(() => {
  const click = () => console.log();
  return (
    <button onClick$={click}>log it</button>
  );
});
```

Event handler must be wrapped with ${ ... }.

#### mutableIdentifier

Examples of correct code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const HelloWorld = component$(() => {
  const person = { name: 'Bob' };
 
  return (
    <button onClick$={() => {
      person.name = 'Alice';
    }}>
      {person.name}
    </button>
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const HelloWorld = component$(() => {
  let personName = 'Bob';
 
  return (
    <button onClick$={() => {
      personName = 'Alice';
    }}>
      {personName}
    </button>
  );
});
```

Simple values are not allowed to be mutated. Use an Object instead and edit one of its property.

### loader-location

#### invalidLoaderLocation

Examples of correct code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

Examples of incorrect code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

This is not a valid location for a route loader. It only can be used inside the src/routes folder, in a layout.tsx or index.tsx file.

#### missingExport

Examples of correct code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

Examples of incorrect code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
const useProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

The route loader function must be exported.

#### wrongName

Examples of correct code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

Examples of incorrect code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const getProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

The route loader function name must start with use.

#### recommendedValue

Examples of correct code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useProductDetails = routeLoader$(async (requestEvent) => {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
});
```

Examples of incorrect code for this rule:

```
import { routeLoader$ } from '@builder.io/qwik-city';
 
async function fetcher() {
  const res = await fetch(`https://.../products/${requestEvent.params.productId}`);
  const product = await res.json();
  return product as Product;
}
 
export const useProductDetails = routeLoader$(fetcher);
```

It is recommended to inline the arrow function. This will help the optimizer make sure that no server code is leaked to the client build.

### no-react-props

#### prefer

Examples of correct code for this rule:

```
<MyReactComponent class="foo" for="#password" />;
```

Examples of incorrect code for this rule:

```
<MyReactComponent className="foo" htmlFor="#password" />;
```

Prefer class and for props over className and htmlFor.

### prefer-classlist

#### preferClasslist

Examples of correct code for this rule:

```
import { component$ } from '@builder.io/qwik';
import styles from './MyComponent.module.css';
 
export default component$((props) => {
  // Array syntax example
  return <div class={[
    styles.container, 
    'p-8', 
    props.isHighAttention ? 'text-green-500' : 'text-slate-500',
    { active: true}
  ]}>Hello world</div>;
 
  // Object syntax example
  return <div class={{  
    'text-green-500': props.isHighAttention,
    'p-4': true
  }}>Hello world</div>;
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
import classnames from 'classnames';
import styles from './MyComponent.module.css';
 
export default component$((props) => {
  return <div class={classnames(
    styles.container, 
    'p-8', 
    {
      'text-green-500' : props.isHighAttention,
      'text-slate-500' : !props.isHighAttention,
    },
    { active: true}
  )}>Hello world</div>;
});
```

The class prop should be used instead of any 3rd party lib to efficiently set classes based on an object.

### jsx-no-script-url

#### noJSURL

Examples of correct code for this rule:

```
<button onClick$={() => alert('open the door please')>ring</button>
```

Examples of incorrect code for this rule:

```
<button onClick$="javascript:alert('open the door please')">ring</button>
```

### jsx-key

#### missingIterKey

Examples of correct code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const Person = component$(() => {
  const person  = {
    firstName: 'John',
    lastName: 'Doe',
    age: 32,
  }
 
  return (
    <ul>
      {Object.keys(person).map((color) => (
        <li key={`person-${key}`}>{person[key]}</li>
      )}
    </ul>
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const Person = component$(() => {
  const person  = {
    firstName: 'John',
    lastName: 'Doe',
    age: 32,
  }
 
  return (
    <ul>
      {Object.keys(person).map((color) => (
        <li>{person[key]}</li>
      )}
    </ul>
  );
});
```

Missing key prop for element in iterator.

#### missingIterKeyUsePrag

Examples of correct code for this rule:

```
import { component$ } from '@builder.io/qwik';
import Card from './Card';
import Summary from './Summary';
 
export const Person = component$(() => {
  const person  = {
    firstName: 'John',
    lastName: 'Doe',
    age: 32,
  }
 
  return (
    {Object.keys(person).map((color) => (
      <Fragment key={`person-${key}`}>
        <Card value={person[key]} />
        <Summary value={person[key]} />
      </Fragment>
    )}
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
import Card from './Card';
import Summary from './Summary';
 
export const Person = component$(() => {
  const person  = {
    firstName: 'John',
    lastName: 'Doe',
    age: 32,
  }
 
  return (
    {Object.keys(person).map((color) => (
      < key={`person-${key}`}>
        <Card value={person[key]} />
        <Summary value={person[key]} />
      </>
    )}
  );
});
```

Missing key prop for element in iterator. The key prop allows for improved rendering performance. Shorthand fragment syntax does not support providing keys. Use <Fragment> instead

#### missingArrayKey

Examples of correct code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const ColorList = component$(() => {
  const colors = ['red', 'green', 'blue'];
 
  return (
    <ul>
      {colors.map((color) => (
        <li key={`color-${color}`}>{color}</li>
      )}
    </ul>
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const ColorList = component$(() => {
  const colors = ['red', 'green', 'blue'];
 
  return (
    <ul>
      {colors.map((color) => (
        <li>{color}</li>
      )}
    </ul>
  );
});
```

Missing key prop for element in array. The key prop allows for improved rendering performance.

#### missingArrayKeyUsePrag

Examples of correct code for this rule:

```
import { component$, Fragment } from '@builder.io/qwik';
 
export const ColorList = component$(() => {
  const colors = ['red', 'green', 'blue'];
 
  return (
    {colors.map((color) => (
      <Fragment key={`color-${color}`}>
        <h2>{color}</h2>
        <p>The color "${color}" is a great color.</p>
      </Fragment>
    )}
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const ColorList = component$(() => {
  const colors = ['red', 'green', 'blue'];
 
  return (
    {colors.map((color) => (
      < key={`color-${color}`}>
        <h2>{color}</h2>
        <p>The color "${color}" is a great color.</p>
      </>
    )}
  );
});
```

Missing key prop for element in array. The key prop allows for improved rendering performance. Shorthand fragment syntax does not support providing keys. Use <Fragment> instead

#### nonUniqueKeys

Examples of correct code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const ColorList = component$(() => {
  const colors = ['red', 'green', 'blue'];
 
  return (
    <ul>
      {colors.map((color) => (
        <li key={`color-${color}`}>{color}</li>
      )}
    </ul>
  );
});
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
 
export const ColorList = component$(() => {
  const colors = ['red', 'green', 'blue'];
 
  return (
    <ul>
      {colors.map((color) => (
        <li key="not-a-good-idea">{color}</li>
      )}
    </ul>
  );
});
```

The key prop must be unique.

### unused-server

#### unusedServer

Examples of correct code for this rule:

```
import { $, component$ } from '@builder.io/qwik';
import { server$ } from '@builder.io/qwik-city';
 
const serverGreeter = server$((firstName: string, lastName: string) => {
  const greeting = `Hello ${firstName} ${lastName}`;
  return greeting;
});
 
export default component$(() => (
    <button
      onClick$={$(async () => {
        const greeting = await serverGreeter('John', 'Doe');
        alert(greeting);
      })}
    >
      greet
    </button>
  );
);
```

Examples of incorrect code for this rule:

```
import { component$ } from '@builder.io/qwik';
import { server$ } from '@builder.io/qwik-city';
 
const serverGreeter = server$((firstName: string, lastName: string) => {
  const greeting = `Hello ${firstName} ${lastName}`;
  return greeting;
});
 
export default component$(() => (
    <button
      onClick$={async () => {
        const greeting = 'not using the server$ function';
        alert(greeting);
      }}
    >
      greet
    </button>
  );
);
```

A server$ function is declared, but never used.

### jsx-img

#### noLocalSrc

Examples of correct code for this rule:

```
import Image from '~/media/image.png';
<Image />
```

Examples of incorrect code for this rule:

```
<img src="/image.png">
```

Serving images from public are not optimized, nor cached. Import images using ESM instead.

#### noWidthHeight

Examples of correct code for this rule:

```
<img width="200" height="600" src="/static/images/portrait-01.webp">
```

Examples of incorrect code for this rule:

```
<img src="/static/images/portrait-01.webp">
```

For performance reasons, always provide width and height attributes for <img> elements, it will help to prevent layout shifts.

### jsx-a

#### noHref

### no-use-visible-task

#### noUseVisibleTask

### Contributors

Thanks to all the contributors who have helped make this documentation better!
