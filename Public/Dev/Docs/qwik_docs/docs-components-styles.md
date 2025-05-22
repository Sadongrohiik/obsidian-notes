# https://qwik.dev/docs/components/styles/

[Original link](https://qwik.dev/docs/components/styles/)

# Styles

Qwik does not enforce a specific styling approach, you can style your Qwik app using any method you prefer, such as CSS, CSS-in-JS, CSS modules...

## CSS Modules

Qwik supports CSS Modules out of the box thanks to Vite.

To use CSS modules, simply create a .module.css file. For example, MyComponent.module.css and import it in your component.

```
.container {
  background-color: red;
}
```

Then, import the CSS module in your component.

```
import { component$ } from '@builder.io/qwik';
import styles from './MyComponent.module.css';
 
export default component$(() => {
  return <div class={styles.container}>Hello world</div>;
});
```

Remember that Qwik uses class instead of className for CSS classes.

Qwik also accepts arrays, objects, or a combination of them to assign multiple classes:

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

## Global Styles

Many apps use a global stylesheet for browser resets and defining global styles. This is a good practice, but it is not recommended to use it for styling your components. Qwik is optimized to let the browser download the styles that are needed for the current view. If you use a global stylesheet, all of the styles will be downloaded on the first load, even if they are not needed for the current view.

```
import './global.css';
```

Automatically, Qwik will try to inline this file in production mode if the amount of CSS is less than 10KB. If the file is larger than 10KB, it will be loaded as a separate file.

## CSS-in-JS

Qwik has first-class CSS-in-JS support using styled-vanilla-extract, which provides an extremely efficient css-in-js solution without any runtime!

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
import { component$ } from '@builder.io/qwik';
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

Please refer to the docs of our official integration for more information.

How about emotion or other CSS-in-JS libs? While extremely popular, emotion and other CSS-in-JS libs are not the best choice for Qwik. They are not optimized for runtime performance and they don't have a good SSR streaming support, leading to a degraded server and client performance.

## Styled-components

The styled-components library is a popular tool in React-land for writing CSS-in-JS. Thanks to the same styled-vanilla-extract plugin, you can write your styles with styled-components syntax in Qwik with zero-runtime cost!

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

Like this:

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
import { component$ } from '@builder.io/qwik';
import { BlueBox } from './styles.css';
 
export const Cmp = component$(() => {
  return <BlueBox />;
});
```

## Scoped CSS

To use scoped CSS, you can use the useStylesScoped$() hook exported from @builder.io/qwik.

useStylesScoped$() uses emojis to set a unique name on the selector. This is added by Qwik to avoid CSS name / selector clashes, and to ensure that the styles are correctly scoped as expected..

```
import { component$, useStylesScoped$ } from '@builder.io/qwik';
 
export default component$(() => {
  useStylesScoped$(`
    .container {
      background-color: red;
    }
  `);
  return <div class="container">Hello world</div>;
});
```

You can also import an external CSS file. For that you need to add the ?inline query parameter to the import of the CSS file, and pass the default export of the CSS file to the useStyleScoped$() hook.

```
.container {
  background-color: red;
}
```

```
import { component$, useStylesScoped$ } from '@builder.io/qwik';
 
import styles from './MyComponent.css?inline';
 
export default component$(() => {
  useStylesScoped$(styles);
  return <div class="container">Hello world</div>;
});
```

### :global() selector

Using useStylesScoped$ will scope all child selectors in a ruleset to the component. If you need to style child components rendered through a <Slot />, you will need to break out of the scoped styles using the :global() selector.

```
import { useStylesScoped$, component$ } from '@builder.io/qwik';
 
export const List = component$(() => {
  useStylesScoped$(`
    .list {
      display: flex;
 
      > :global(*nth-child(3)) {
        width: 100%
      }
    }
  `);
 
  return (
    <div class="list">
      <Slot />
    </div>;
  );
});
```

This will render a css selector of .list.⭐️8vzca0-0 > *:nth-child(3), allowing you to target child components. This could be considered the equivalent of using ::ng-deep in Angular.

Beware that this may have unintended effects that cascade down your component tree.

## useStyles$()

A lazy-loadable reference to component's styles.

Component styles allow Qwik to lazy load the style information for the component only when needed, which avoids double loading during SSR hydration.

```
import { useStyles$, component$ } from '@builder.io/qwik';
import styles from './code-block.css?inline';
 
export const CmpStyles = component$(() => {
  useStyles$(styles);
  return <span class="my-text">Some text</span>;
});
```

```
// code-block.css
.my-text {
  color: red;
}
```

Notice that in order to import CSS as a string in Vite, you need to add the ?inline query parameter to the import, like this: import styles from './code-block.css?inline';

useStyles$ uses lazy loading strings that won't dynamically update. If you'd like to evaluate some JS, use a style tag instead

```
export const CmpStyles = component$(() => {
  const primaryColor = "red";
 
  // ❌ Does not work
  useStyles$(`
    .my-text {
      --primary-color: ${primaryColor};
    }
  `);
 
  // ✅ Adding in the style attribute works
  return (
    <span 
      style={{ "--primary-color": primaryColor }} 
      class="my-text"
    >
      Some text
    </span>
  );
});
```

## CSS Preprocessors

Thanks to Vite, Qwik supports CSS preprocessors like Sass, Less, Stylus, and PostCSS.

There is no need to install Qwik-specific plugins for them, but the corresponding pre-processor itself must be installed:

```
# .scss and .sass
pnpm add -D sass
 
# .less
pnpm add -D less
 
# .styl and .stylus
pnpm add -D stylus
```

```
# .scss and .sass
npm add -D sass
 
# .less
npm add -D less
 
# .styl and .stylus
npm add -D stylus
```

```
# .scss and .sass
yarn add -D sass
 
# .less
yarn add -D less
 
# .styl and .stylus
yarn add -D stylus
```

```
# .scss and .sass
bun add -D sass
 
# .less
bun add -D less
 
# .styl and .stylus
bun add -D stylus
```

Check Vite's docs for more information.

## Tailwind

To use Tailwind in your app, you can add it to your app with our built-in integration:

```
pnpm run qwik add tailwind
```

```
npm run qwik add tailwind
```

```
yarn run qwik add tailwind
```

```
bun run qwik add tailwind
```

Check out the integration docs for more information.

## PostCSS

It is also possible to use PostCSS in your app with our built-in integration:

```
pnpm run qwik add postcss
```

```
npm run qwik add postcss
```

```
yarn run qwik add postcss
```

```
bun run qwik add postcss
```

Important: Since we are using vite, the configuration should look as follows to work:

```
// Configuration with vite
module.exports = {
  plugins: {
    autoprefixer: {},
    "postcss-preset-env": {
      stage: 3,
      features: {
        "nesting-rules": true,
      },
    },
  },
}
```

Now you will be able to use CSS with nesting-rules like the following ones:

```
body {
  & .box {
    background: red;
 
    &:hover {
      background: yellow;
    }
  }
}
```

Check out the integration docs for more information.

## Why not inline styles using the <style> tag?

A naive way to ensure that a component has the correct styles loaded is to inline the style information into a component like so.

```
export const MyComponent = () => {
  return (
    <>
      <style>.my-class { color: red; }</style>
      My Component
    </>
  );
}
```

The problem with this approach is that we will load styles twice.

What is needed is to load the styles independently from the component. This is what useStyles$() is for. There are two scenarios:

### Contributors

Thanks to all the contributors who have helped make this documentation better!
