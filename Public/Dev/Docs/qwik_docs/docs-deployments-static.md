# https://qwik.dev/docs/deployments/static/

[Original link](https://qwik.dev/docs/deployments/static/)

# Static Site Adapter

Qwik's Static Site adapter helps to generate static html files which can be easily deployed to any cloud providers.

## Installation

To integrate the static-site adapter, use the add command:

```
pnpm run qwik add static
```

```
npm run qwik add static
```

```
yarn run qwik add static
```

```
bun run qwik add static
```

Above command will create a directory at project root named adapters/static/vite.config.ts with the below code.

```
import { staticAdapter } from "@builder.io/qwik-city/adapters/static/vite";
import { extendConfig } from '@builder.io/qwik-city/vite';
import baseConfig from '../../vite.config';
 
export default extendConfig(baseConfig, () => {
  return {
    build: {
      ssr: true,
      rollupOptions: {
        input: ['@qwik-city-plan'],
      },
    },
    plugins: [
      staticAdapter({
        origin: 'https://yoursite.qwik.dev',
      }),
    ],
  };
});
```

Remember to change the origin in this file to your domain.

Now, you can generate static site while using Qwik's rich ecosystem, file based routing and many more.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
