# https://qwik.dev/docs/deployments/vercel-edge/

[Original link](https://qwik.dev/docs/deployments/vercel-edge/)

# Vercel Edge Adapter

Qwik City Vercel Edge adapter allows you to connect Qwik City to Vercel Edge Functions.

## Installation

To integrate the vercel-edge adapter, use the add command:

```
pnpm run qwik add vercel-edge
```

```
npm run qwik add vercel-edge
```

```
yarn run qwik add vercel-edge
```

```
bun run qwik add vercel-edge
```

It will automatically install the required dependencies, including the Vercel CLI.

The adapter will add a new vite.config.ts within the adapters/ directory, and a new entry file will be created, such as:

```
└── adapters/
    └── vercel-edge/
        └── vite.config.ts
└── src/
    └── entry.vercel-edge.tsx
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

Notice that you might need a Vercel account in order to complete this step!

## Production deploy

After installing the integration the project is ready to be deployed to Vercel. However, you will need to create a git repository and push the code to it.

Please refer to the Vercel docs for more information on how to deploy your site: Vercel docs

### Environment variables

You can access environment variables from Vercel like this process.env['MY_ENV_VAR']

## Advanced

### Vercel Edge Entry Middleware

When the vercel-edge adapter is added, a new entry file will be created at src/entry.vercel-edge.tsx. Below is an example of using the built-in middleware within the entry file.

```
import { createQwikCity } from '@builder.io/qwik-city/middleware/vercel-edge';
import qwikCityPlan from '@qwik-city-plan';
import render from './entry.ssr';
 
export default createQwikCity({ render, qwikCityPlan });
```

The compiled middleware will be built in the .vercel/output directory.

### Vercel Edge Functions

Vercel Edge Functions are deployed globally by default on Vercel's Edge Network and enable you to move server-side logic to the Edge, close to your visitor's origin.

Edge Functions use the Vercel Edge Runtime, which is built on the same high-performance V8 JavaScript and WebAssembly engine that is used by the Chrome browser. By taking advantage of this small runtime, Edge Functions can have faster cold boots and higher scalability than Serverless Functions.

Edge Functions run after the cache, and can both cache and return responses.

### Drizzle with Vercel Edge Functions

Running Postgres on edge requires edge-compatible drivers since Postgres relies on Node.js APIs.
When no adapter is used, the below errors might appear during the deployment process:

```
└── The Edge Function "_qwik-city" is referencing unsupported modules
└── Cannot bundle Node.js built-in "node:events" imported from "node_modules\postgres\cf\polyfills.js"
```

Luckily, drizzle has a section that can be followed to implement the right adapter of choice.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
