# https://qwik.dev/docs/integrations/styled-vanilla-extract/

[Original link](https://qwik.dev/docs/integrations/styled-vanilla-extract/)

# Styled Vanilla Extract

Styled-vanilla-extract is a CSS framework built on top of vanilla-extract that delivers a modern and performant CSS-in-JS with Zero-runtime.

This integration supports two ways of styling:

## Usage

You can add styled-vanilla-extract easily by using the following Qwik starter script:

```
pnpm run qwik add styled-vanilla-extract
```

```
npm run qwik add styled-vanilla-extract
```

```
yarn run qwik add styled-vanilla-extract
```

```
bun run qwik add styled-vanilla-extract
```

After the installation a new route will be created in your project, showcasing the usage of the library in a new component.

### The Vanilla Extract way

Please refer to the official docs for more information about Vanilla Extract.

```
import { style } from 'styled-vanilla-extract/qwik';
 
export const blueClass = style({
  display: 'block',
  width: '100%',
  height: '500px',
  background: 'blue',
});
```

```
import { blueClass } from './styles.css';
 
export const Cmp = component$(() => {
  return <div class={blueClass} />;
});
```

```
pnpm run qwik add styled-vanilla-extract
```

```
npm run qwik add styled-vanilla-extract
```

```
yarn run qwik add styled-vanilla-extract
```

```
bun run qwik add styled-vanilla-extract
```

How about emotion or other CSS-in-JS libs? While extremely popular, emotion and other CSS-in-JS libs are not the best choice for Qwik. They are not optimized for runtime performance and they don't have a good SSR streaming support, leading to a degraded server and client performance.

## Styled-components

Using the same integration, you have a styled-components powered by Vanilla Extract, use the exported styled function to create your components.

```
import { styled } from 'styled-vanilla-extract/qwik';
 
export const BlueBox = styled.div`
  display: block;
  width: 100%;
  height: 500px;
  background: blue;
`;
```

```
import { BlueBox } from './styles.css';
 
export const Cmp = component$(() => {
  return <BlueBox />;
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
