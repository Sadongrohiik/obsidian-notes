# https://qwik.dev/docs/advanced/custom-build-dir/

[Original link](https://qwik.dev/docs/advanced/custom-build-dir/)

# Custom Build Output Directory

By default, the build output directory for Qwik is the dist folder in the root folder of the project.

In certain cases, we may need to make the build output directory different from the default package.

## Wrong Way

Usually with Vite.js we do it like this:

```
import { defineConfig } from 'vite';
import { qwikVite } from '@builder.io/qwik/optimizer';
import { qwikCity } from '@builder.io/qwik-city/vite';
import { resolve } from 'node:path';
/* VITE_IMPORTS */
 
export default defineConfig(() => {
  const pagesDir = resolve('pages');
 
  return {
    /* VITE_CONFIG */
    build: {
      outDir: '../resources/', // This will be overrided to `dist` by qwikVite() setting
    },
    plugins: [
      qwikCity({
        pagesDir,
        layouts: {
          default: resolve('src', 'layouts', 'default', 'default.tsx'),
        },
      }),
      qwikVite(/* VITE_QWIK */),
      /* VITE_PLUGINS */
    ],
  };
});
```

However, it will be overridden by the settings of QwikVite() so nothing happens and the build output directory is still in the dist folder

## The Right Way

So instead of changing the settings in Vite.js directly, we just need to change the settings in QwikVite() like this:

```
import { defineConfig } from 'vite';
import { qwikVite } from '@builder.io/qwik/optimizer';
import { qwikCity } from '@builder.io/qwik-city/vite';
import tsconfigPaths from 'vite-tsconfig-paths';
 
export default defineConfig(() => {
  return {
    ssr: { target: 'webworker', noExternal: true },
    plugins: [
      qwikCity(),
      qwikVite({
        client: {
          outDir: 'resources/', // This is the right setting
        },
      }),
      tsconfigPaths(),
    ],
  };
});
```

So that the output build directory becomes resources, please rename this folder name as needed.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
