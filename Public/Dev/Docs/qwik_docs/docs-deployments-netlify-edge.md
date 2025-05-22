# https://qwik.dev/docs/deployments/netlify-edge/

[Original link](https://qwik.dev/docs/deployments/netlify-edge/)

# Netlify Edge Adapter

Qwik City Netlify Edge adapter allows you to connect Qwik City to Netlify Edge Functions.

## Installation

To integrate the netlify-edge adapter, use the add command:

```
pnpm run qwik add netlify-edge
```

```
npm run qwik add netlify-edge
```

```
yarn run qwik add netlify-edge
```

```
bun run qwik add netlify-edge
```

It will automatically install the required dependencies, including the Netlify CLI.

The adapter will add a new vite.config.ts within the adapters/ directory, and a new entry file will be created, such as:

```
└── adapters/
    └── netlify-edge/
        └── vite.config.ts
└── src/
    └── entry.netlify-edge.tsx
```

Additionally, within the package.json, the build.server and deploy scripts will be updated.

## Production build

To build the application for production, use the build command, this command will automatically run build.server and build.client:

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

Read the full guide here

## Dev deploy

To deploy the application for development:

```
pnpm run deploy
```

```
npm run deploy
```

```
yarn run deploy
```

```
bun run deploy
```

Notice that you might need a Netlify account in order to complete this step!

## Production deploy

After installing the integration the project is ready to be deployed to Netlify. However, you will need to create a git repository and push the code to it.

Please refer to the Netlify docs for more information on how to deploy your site: Netlify docs

## Advanced

### Netlify Edge Entry Middleware

When the netlify-edge adapter is added, a new entry file will be created at src/entry.netlify-edge.tsx. Below is an example of using the built-in middleware within the entry file.

```
import { createQwikCity } from '@builder.io/qwik-city/middleware/netlify-edge';
import qwikCityPlan from '@qwik-city-plan';
import render from './entry.ssr';
 
export default createQwikCity({ render, qwikCityPlan });
```

The compiled middleware will be built in the .netlify/edge-functions directory.

### Netlify Edge Functions Declarations

Netlify Edge Functions declarations can be configured to run on specific URL patterns. Each edge function declaration associates one site path pattern with one function to execute on requests that match the path. A single request can execute a chain of edge functions from a series of declarations. A single edge function can be associated with multiple paths across various declarations.

This is useful to determine if a page response should be Server-Side Rendered (SSR) or if the response should use a static-site generated (SSG) index.html file instead.

By default, the Netlify Edge adapter will generate a .netlify/edge-middleware/manifest.json file, which is used by the Netlify deployment to determine which paths should, and should not, use edge functions.

To override the generated manifest, you can add a declaration to the netlify.toml using the [[edge_functions]] config. For example:

```
[[edge_functions]]
  path = "/admin"
  function = "auth"
```

### Netlify Request Context

Netlify context is available in endpoint method's platform param:

```
export const onRequest = async ({ platform }) => {
  platform.log('requested ip:', platform.ip);
};
```

### Environment variables

```
export const onRequest = async ({ env }) => {
  platform.log('netlify serverless env read from Netlify UI or CLI', env.get('API_KEY'));
};
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
