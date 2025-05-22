# https://qwik.dev/docs/integrations/tailwind/

[Original link](https://qwik.dev/docs/integrations/tailwind/)

# Tailwind

Tailwind is a CSS framework that provides us with single-purpose utility classes which are
opinionated for the most part, and which help us design our web pages from right inside our
markup or .js/.jsx/.ts/.tsx/.mdx files. Tailwindcss Website

This page contains updated instructions for tailwind v4. If you need to use tailwind v3, you can find the relevant documentation here.

## Usage

You can add Tailwind v4 easily by using the following Qwik starter script:

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

The previous command updates your app with the necessary dependencies,
and modifies the following files

```
@import "tailwindcss";
 
/* ... other css stuff ... */
 
/* ... to customize tailwind follow guidelines at https://tailwindcss.com/docs/theme ... */
 
/* Explicitly registering sources */
/* @source "../node_modules/@your/ui-lib"; */
 
/* Setting your base path */
/* @import "tailwindcss" source("../src"); */
 
/* Disabling automatic detection of source file */
/* @import "tailwindcss" source(none); */
```

```
import { defineConfig , type UserConfig} from 'vite'
import tailwindcss from '@tailwindcss/vite'
// … other imports ...
 
export default defineConfig(({ command, mode }): UserConfig => {
  return {
    plugins: [
      tailwindcss(),
      // ... other plugins ...
      ]
    // ... other stuff ...
    }
  }
)
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
