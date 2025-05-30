# https://qwik.dev/docs/advanced/library/

[Original link](https://qwik.dev/docs/advanced/library/)

# Library

Qwik uses the library mode of Vite to create component libraries.

In order to create a component library for Qwik, you need to make sure of specific rules, this is because the Qwik Optimizer needs to recognize your library as a Qwik library.

The easiest way to create a new component library is to use the build-in library starter:

```
pnpm create qwik library my-library
```

```
npm create qwik library my-library
```

```
yarn create qwik library my-library
```

```
bun create qwik library my-library
```

This will create a new folder called my-library with the following structure:

```
├── README.md
├── package.json
├── src
│   ├── components
│   │   ├── counter
│   │   │   └── counter.tsx
│   │   └── logo
│   │       └── logo.tsx
│   ├── entry.dev.tsx
│   ├── entry.ssr.tsx
│   ├── index.ts
│   └── root.tsx
├── tsconfig.json
└── vite.config.ts
```

The most important files of a library are a properly configured package.json and vite.config.ts.

## package.json

```
{
  "name": "my-qwik-library-name",
  "version": "0.0.1",
  "description": "Create a reusable Qwik component library",
  "main": "./lib/index.qwik.mjs",
  "qwik": "./lib/index.qwik.mjs",
  "types": "./lib-types/index.d.ts",
  "exports": {
    ".": {
      "import": "./lib/index.qwik.mjs",
      "require": "./lib/index.qwik.cjs",
      "types": "./lib-types/index.d.ts"
    }
  },
  "files": [
    "lib",
    "lib-types"
  ],
  "type": "module",
}
```

Notice the qwik field, this is the entry point for the Qwik Optimizer, it will use this file to generate the index.qwik.mjs file.

The file must be called with the .qwik.mjs extension, otherwise the Qwik Optimizer will not recognize it.

## vite.config.ts

```
import { defineConfig } from 'vite';
import { qwikVite } from '@builder.io/qwik/optimizer';
 
export default defineConfig(() => {
  return {
    build: {
      target: 'es2020',
      lib: {
        entry: './src/index.ts',
        formats: ['es', 'cjs'],
        fileName: (format) => `index.qwik.${format === 'es' ? 'mjs' : 'cjs'}`,
      },
    },
    plugins: [qwikVite()],
  };
});
```

Compared to a normal Vite configuration, libraries will use the lib mode of Vite, which requires you to properly configure build.lib.

## src/index.ts

This is the entry point of your library, it will export all the components, and functions that you want to expose to the world.

```
// As an example, we will export the Logo and Counter components
export { Logo } from './components/logo/logo';
export { Counter } from './components/counter/counter';
```

## Libraries are also Apps

The library starter is also a standalone Qwik app (without routing, nor Qwik City), this is the reason why you will find entry.dev.tsx, entry.ssr.tsx and root.tsx files.

Do not worry about them, they won't be part of the final library, but they are useful during development and testing, so you can test your components in a real Qwik app.

## Build and publish

In order to publish your library, you have to first build it in lib mode and then publish to npm.

```
pnpm run build
```

```
npm run build
```

```
yarn run build
```

```
bun run build
```

This will create a lib folder with the following structure. Then you can publish it to npm.

```
npm publish
```

Notice that before first publishing, you might want to update the package.json fields, like name, version, description, etc.

For any other subsequent publish, you will need to update the version field.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
